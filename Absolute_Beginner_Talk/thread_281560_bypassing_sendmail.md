---
title: "bypassing sendmail"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-10-21
Hello you,

The next script cann't send a message to a mail addresse by "Yahoo" (someone@yahoo.com) but wel to a mail addresse by google (someone@gmail.com).
```
<html>

<head>
<title>Exercise 14.2</title>
</head>

<body>
<div>
<form method="post" action="<?=$_SERVER['PHP_SELF']?>">
<p>
Insert your mail address: <input type="text" name="mail">
</p>
<p>
Insert the subject: <input name="subject" type="text">
</P>
<p>
<textarea name="message" row="50px" col="70px">
</textarea>
</p>
<p>
<input type="submit" value="Submit">
</p>
</form>
</div>

<?php
$to="someone@yahoo.com";
$from=$_REQUEST['mail'];
$subject=$_REQUEST['subject'];
$message=$_REQUEST['message'];
if (!empty($from) && !empty($subject) && !empty($message)){
 mail($to, $subject, $message, "From: $from\r\n") or die("Couldn't send mail");
 print "Browser: ".$_SERVER['HTTP_USER_AGENT']."<br>IP address: ".$_SERVER['REMOTE_ADDR'];
}
else {
 print "You haven't filled in the form completely!";
}
?>
```
Could you help me please?

Thanks,

---

### Post by Kurt` on 2006-10-21
Are you hosting a sendmail server off your local computer? Most major webmail places block emails that aren't from fully-qualified domain names... if they see email from w-x-y-z.yourisp.com, they assume it's an infected Windows machine...

---

### Post by linux-beginner on 2006-10-21
I'm hosting my local computer. What is the solution?

---

