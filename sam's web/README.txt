
Form elements with a little javascript.

We need to create a login page for our client: Hermaneutics. The page needs to have a form that contains a
text input box for the user's log in and a text box for the password. 

There will also be a reset button to reset the text boxes, and a submit button to submit the form.

The file:

testLoginForm.html

1) *(optional) Create a stylesheet file called formTest.css and add a link to this file in the html page.

2) Add a style rule for the h2 element that aligns the text in the center and color #707070. Save and test.

3) Now add a form to the html page:
    <form name="loginForm" action="#" method="post">
  
   Don't forget to add a closing form tag </form>

4) Now, within the form tags, add a text input and a password input:

   The text input has a name and id attribute "login", and the password input has a name and id attribute "password".

5) Add labels to go with the two input boxes.

   One label for the "login" with text "Login: "
   and one label for the "password" with text "Password: "


6) Next, add two inputs: a submit (type="submit") and a button (type="button").
   The submit has name and id "submit" and value "Log in".
   The button has name and id "reset" and value "Reset".

   Save and test: you should see the labels, text boxes and buttons in a horizontal row.

7) Now its time for some javascript. We want to do a little form validation: check that the log in and
   password boxes are not blank when the user clicks the submit. 

   We will define a validateLoginForm function to do this. 
   In the head section of the page, add these tags:

   <script type="text/javascript">
   </script>

   Now add this javascript code inside the script tags:

   function validateForm()
   {
      var login=document.forms["loginForm"]["login"].value;
      var pwd=document.forms["loginForm"]["password"].value;

      if (login==null || login=="")  {
         alert("Please enter a login");
         return false;
       }
      if (pwd==null || pwd=="")  {
         alert("Please enter a password");
         return false;
      }
   }

  This code uses the DOM to locate the input boxes by name and retrieve their current values.
  If they are empty an alert will be shown and the form will not be submitted to the server.


8) Now, in the form tag, add a call to the javascript validation function that is triggered by the submit event:
       onsubmit="return validateForm()"

   so it now looks like this: <form name="loginForm" action="#" onsubmit="return validateForm()" method="post">

   Now save and test. The submit button triggers the form's "onsubmit" handler- a call to our validate function.
   If that call returns false the form does not submit.

9) Now it's time to hook up the reset button. Define another function in the script area in the head section:

   function resetLoginForm()
   {
      document.forms["loginForm"]["login"].value="";
      
   }

   This code will use the DOM in the same way as before to locate the login text box and set its value to be empty (the empty string).


10) Now we want to activate this function when the reset button is clicked. Add this call to the reset button tag: onclick="resetLoginForm()".
    Save and test. If you type something in the login box and click Reset the box should clear.

    You may now add the code in the resetLoginForm function that clears the password box.


11) *(optional) Now we can move the javascript code to its own file. Create a file called formTest.js, then cut and paste the javascript
   from the head section of the html file into the js file. Delete the <script> tags. Then add a link to the js file in the head section:
   <script type="text/javascript" src="formTest.js"></script>
   Note: IE needs both styles and javascript to be embedded to work due to its security policy. It does wok with linked files in a server context however.

12) Now it's time to style the form so that it looks better. There are many ways to do this. We use tables and css.
    First, enclose the form in a div referencing the "login-wrapper" id style.

13) Enclose the two labels and text boxes in a 2x2 table, each control in a td cell.

14) in IE you will notice that the password text box is shorter than the regular text box. IE renders the password
    control with different padding, etc. So, have the text and password inputs reference a class called "fixed-input-box".
    Add this style definition to the css:

 
.fixed-input-box {
  width: 200px;
  font-family: sans-serif;
  font-size: 15px;
  padding: 3px;
  border: 1px solid black;
}


15) Define a descendant style for the table in the login-wrapper that sets the width to 400 pixels.

16) Add a fieldset tag that encloses the form but it inside the login-wrapper. Add a legend to the fieldset with text "Login Form".

    In the css file, add descendant style definitions for the fieldset and legend:

fieldset 
   border-style:solid;
   border-color: #dddddd;
   border-width:5px;
   width:400px;
   margin: auto;


legend 
  color: #999999;
  font-style: italic;
  font-weight: bold;
  font-size: 1.0em;

17) Now we'll work on the buttons. Wrap the buttons ina div that references the id style "loginButtons".
    Enclose the buttons in a 1x2 table, with each button in a td cell.

    Create a style definition in the stylesheet for loginButtons with width 200 pixels. Then center by setting margin
    to auto. 

    Create a descendant style for the button table that also sets the width to 200 pixels.


18) We want the buttons to be farther apart, so we will left-justify the submit button
    within its table cell, and right-justify the reset button in its table cell.

   In the stylesheet define two descendant classes: 

   left-button and right-button, with style rules for text-align left and right, respectively.
   These can be descendants of the login-buttons style.

   Now, in the html file, have the login buttons table cell element reference the appropriate tag; the
   submit button is in the left td element so that td references the left-button class, and the reset button's td
   references the right-button class.

19) Finally, add about 20 pixels of padding to the top of the login buttons div to create a little space between the buttons and the input boxes.


*(optional) Steps 1 and 11 use external files for css and javascript. This is a typical development setup. IE will work on the local machine
            only if the styles and code are embedded. 