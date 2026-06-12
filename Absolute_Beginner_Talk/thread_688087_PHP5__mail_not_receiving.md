---
title: "PHP5 / mail not receiving"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by pteri498 on 2008-02-05
I'm using the w3 tutorials for php.

I'm running Ubuntu 7.10 with Apache 2 and PHP 5 installed after the base system was installed, so possibly it wasn't all preconfigured like I would have liked it.

Anyway, I'm trying to send mail through my web page to another e-mail, but at both hotmail and comcast, it's not being received. Here's my code:

```

<html>
<body>

<?php
if (isset($_REQUEST['email']))
//if "email" is filled out, send email
  {
  //send email
  $email = $_REQUEST['email'] ; 
  $subject = $_REQUEST['subject'] ;
  $message = $_REQUEST['message'] ;
  mail( "********@comcast.net", "Subject: $subject",
  $message, "From: $email" );
  echo "Thank you for using our mail form";
  }
else
//if "email" is not filled out, display the form
  {
  echo "<form method='post' action='mail.php'>
  From Email: <input name='email' type='text' /><br />
  Subject: <input name='subject' type='text' /><br />
  Message:<br />
  <textarea name='message' rows='15' cols='40'>
  </textarea><br />
  <input type='submit' />
  </form>";
  }
?>

</body>
</html>

```

Any idea why it's not being received? I'm not sure whether or not it's even sending. Do I need to set up an SMTP server or something?

Thanks.

---

### Post by tosk on 2008-02-05
You should install an SMTP server to send mail to outside domains. Postfix is relatively straightforward on Ubuntu. It's even in the server guide for 7.10 in the Community Docs.

Once that's installed, you might still have an issue with mail not being able to connect to remote SMTP servers. If that happens, you'll need to setup Postfix to relay through your ISP's mail server.

---

