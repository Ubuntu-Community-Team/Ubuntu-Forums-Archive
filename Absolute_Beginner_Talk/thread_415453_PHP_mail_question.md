---
title: "PHP mail question"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by syvehc on 2007-04-20
Hi,

I was wondering if someone could explain how to send mail using PHP.  Here is what I am trying to do, I have a ubuntu 6.10 server running apache 2, mysql, php5 and I want a script to send smtp mail.  I have a working SMTP server and that I would like to use.  Not the Ubuntu box, I know smtp works because I have a scanner that directly sends scans to smtp mail.

Now I would like a php script to send mail and I am not worried about the scripting part of it just the configuration.  I notice that phpmailer seems to be an easy fit, but there seems to be a lack of documentation for a noob like me.  Exactly what do I put in the php.ini, where should the phpmailer extracted class files go in the directory stucture and last they mention includes, but I can't quite grasp if that is a location of the php.ini file or not.

Thanks in advance and I am open to other ideas and packages.

Tom

---

### Post by LaRoza on 2007-04-20
This should be taken to the Programming Talk forum.

[http://www.w3schools.com/php/php_ref_mail.asp](http://www.w3schools.com/php/php_ref_mail.asp)

[http://www.tizag.com/](http://www.tizag.com/) 

has free tutorials.

---

### Post by proalan on 2007-04-20
In the wrong section but heres an example

mail("john@example.com", "An HTML Message", $body, $headers); 

the prototype is

mail($toAddress,$subjectMessage,$bodyMessage,$fromAddress)

works fine so long as your mail server is configured properly and your ISP allows use of port 25 to send mails.

---

### Post by syvehc on 2007-04-20
Sorry, wouldn't it be more of a configuration rather than programming.  I just want to confirm and configure the mail function works and let the programmer configure the PHP.  PHPMailer is just leaving me confused with trying a simple php test file.  I know I need to add something to the php.ini and I am unsure where.  I also am confused to where to extract the PHPMailer files.

---

### Post by proalan on 2007-04-20
just did a google phpmailer.

Is this the script your trying?

[http://phpmailer.sourceforge.net/](http://phpmailer.sourceforge.net/)

---

### Post by syvehc on 2007-04-20
Yes it is and I'm not sure it is the best one to use or not.

Thanks for you help.

---

