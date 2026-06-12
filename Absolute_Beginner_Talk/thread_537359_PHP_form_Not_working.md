---
title: "PHP form Not working"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by kennyn on 2007-08-28
Ok i am pretty sure i have PHP installed correctly on my server. you can go here to see the settings.

[http://www.kennynproductions.com/info.php](http://www.kennynproductions.com/info.php)

Now my question is this. I am trying to get the below HTML form page working. It is pointing to a php page, but after you hit submit it automatically goes to the error page. Below are the links to the form and the link to the php page. Any help would be great.

Form page:
[http://www.maryraymond.net/contact.html](http://www.maryraymond.net/contact.html)

PHP script
[http://www.maryraymond.net/contact.php](http://www.maryraymond.net/contact.php)

Below is the php script:

<?php

// Website Contact Form Generator 

// [http://www.tele-pro.co.uk/scripts/contact_form/](http://www.tele-pro.co.uk/scripts/contact_form/) 

// This script is free to use as long as you  

// retain the credit link  



// get posted data into local variables

$EmailFrom = "kenny@kennyn.com";

$EmailTo = "kenny@kennyn.com";

$Subject = "Contact From Website";

$Name = Trim(stripslashes($_POST['Name'])); 

$Email = Trim(stripslashes($_POST['Email']));

$Phone = Trim(stripslashes($_POST['Phone'])); 

$Message = Trim(stripslashes($_POST['Message'])); 







// prepare email body text

$Body = "";

$Body .= "Name: ";

$Body .= $Name;

$Body .= "\n";

$Body .= "Email Address: ";

$Body .= $Email;

$Body .= "\n";

$Body .= "Phone Number: ";

$Body .= $Phone;

$Body .= "\n";

$Body .= "\n";

$Body .= "\n";

$Body .= "Message: ";

$Body .= $Message;

$Body .= "\n";

$Body .= "\n";

$Body .= "\n";

$Body .= "\n";

$Body .= "End of Contact Form! ";



// send email 

$success = mail($EmailTo, $Subject, $Body, "From: <$EmailFrom>");



// redirect to success page 

if ($success){

  print "<meta http-equiv=\"refresh\" content=\"0;URL=contact_sent.html\">";

}

else{

  print "<meta http-equiv=\"refresh\" content=\"0;URL=error.html\">";

}

?>

---

### Post by jamvegan on 2007-08-28
Try putting an
```
exit();
```
after the first redirect.

---

### Post by hyper_ch on 2007-08-29
and "Trim" should be lower case --> "trim" (although I'm not sure if that is really required)

---

### Post by kennyn on 2007-08-29
Ok i changed the Trim to trim and it still does not work. And if I put exit();. after the if statement and before th else statement the page breaks. Anyone else have any ideas. Thanks

---

### Post by jamvegan on 2007-08-29
I just tested this code, exactly as you posted it.  And it worked.  I didn't have it actually send mail, though.  I replaced the call to mail first with true, and then with false, to see if both redirects worked, and they did.  It also worked if I added the exit() line.  So...are you sure that the mail function is succeeding?

---

### Post by kennyn on 2007-08-30
Is there any possible way you can post or send the different codes that you used. Espically the one with the exit() code in it. I am worried I am doing something wrong. THanks.

---

### Post by svalding on 2007-08-30
If you are trying to send mail out in that script, do you have an MTA installed and configured? It may be erroring because it has no idea what to do with the email piece. Try configuring sendmail or postfix, whichever you prefer to send out the emails.

---

### Post by jamvegan on 2007-08-30
```
// send email

[COLOR="SeaGreen"]$success = true; //mail($EmailTo, $Subject, $Body, "From: <$EmailFrom>");[/COLOR]



// redirect to success page

if ($success){

print "<meta http-equiv=\"refresh\" content=\"0;URL=contact_sent.html\">";
[COLOR="SeaGreen"]exit();[/COLOR]

}

else{

print "<meta http-equiv=\"refresh\" content=\"0;URL=error.html\">";

}
```

I used the entire script, but I'm just posting the section that I made changes to (the green lines).  I also tried it with false instead of true.  I don't have this machine configured to send email, which is why I replaced the call to mail() with true and false, to simulate how the script would work whether mail() was successful or not.

Incidentally, the exit(), strictly speaking, *should* not be necessary, but in some scripts you get unexpected results without it, and used this way it will never *cause* a problem.

---

