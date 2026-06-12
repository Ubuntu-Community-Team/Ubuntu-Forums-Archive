---
title: "How can I Find out whether my webhost/website allows mysql"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-08-16
Hi,
I would like to install and use Drupal on our personal website. Drupal needs mysql, but I don't know whether my webhosting company/ website allows mysql. Their office is currently closed, and i don't want to wait for days to hear back from them. Could you tell me if there's a way to test out by myself whether my website /webhosting company allows mysql?
Perhaps there is some command or some uploaded file that can verify this.

(I'm on Step 2 on [http://drupal.org/node/260](http://drupal.org/node/260))

Thanks.

---

### Post by expatCM on 2007-08-16
Why not have a look on the home page of your host.  Normally they tell you what they are going to supply in a package when you open an account.

You could also have a look at whether your host has Fantastico installed since this will install Drupal or Joomla in one click ....

Have you logged into your host and looked at the Control Panel since this would probably identify mysql, php and phpmyadmin if it is available to you ......

---

### Post by hanzj on 2007-08-16
I can get FTP access to my site at [ftp://ftp.asiteofmine.com/](ftp://ftp.asiteofmine.com/) and use my username and password to log in. But I don't know if I can see the control panel there. How do I get to the control panel?

---

### Post by expatCM on 2007-08-17
When you signed up with your host you were probably sent an email with your username and password.  The same email normally gives you the URL to FTP access, site location, Control Panel location, email settings ...  and related information.  Could you have a look at that email?

Do you have the URL to the hosting company?

---

### Post by hyper_ch on 2007-08-17
well, for drupal you also need php support... so the simplest thing is to create a phpinfo.php file in your account with this content:
```

<?php phpinfo(); ?>

```
And then open it in your browser... if it does not run or just display the source, then you're out of luck... if it runs, it will also tell whether there mysql support.

---

### Post by hanzj on 2007-08-17
[B]Hyper_ch,
I created a phpinfo.php file, uploaded it, and accessed it on the web. It works. 

Please see [http://ubuntuforums.org/attachment.php?attachmentid=41036&d=1187489026](http://ubuntuforums.org/attachment.php?attachmentid=41036&d=1187489026) to see the file itself.
[/B]

---

### Post by EndPerform on 2007-08-17
That's just telling you PHP has SQL support installed.  You're probably going to need to ask your host anyway because you're going to need to know where the database is.  For example, on my site, my provider hosts my database on their DB server, and I had to know details before I could set it up.

What webhost are you with, anyway?

---

### Post by hyper_ch on 2007-08-17
Well, without mysql support in PHP there would be no use to use drupal.

I tend to think as you have mysql support and php you should be able to setup a mysql database somehow. Is there some kind of administrative panel that you can access where you can set what domain you have, where you can setup email accounts and stuff?

---

### Post by hanzj on 2007-08-18
Hi Folks.
I've attached the contents of the php file with 
>  <?php phpinfo(); ?>
inside.
Please see the attached file. I think it says in better terms about SQL and PHP support. I've saved the HTML file in tar.gz format because ubuntuforums won't allow me to upload html files.


My website-hosting company says that they support Drupal, but that we would have to pay more for that service. I wonder if we really have to pay more. Would the attached file tell us whether we already have Drupal compatibility with the way things stand now?

---

### Post by hanzj on 2007-08-18
We're with elhost.com


 [ Nov 13, 2007 Update: Correct Webhosting company is now written in this post]

---

### Post by TooRight on 2007-08-18
Dayummm,  expensive!! :O and they'd want you to pay more?? That's just nuts!! I host all my domains on one account, get a reply to a service ticket within an hour everytime 24/7, have loads of space and bandwidth and stilll pay less than you do :O

I've been with them for over a year and never had a problem, PM if you want their info

Your's looks like a newbie reseller, very amateurish looking site

---

### Post by hyper_ch on 2007-08-19
wow, for 330 mb they charge like  CAD 40?.... for that I get my own root server...

Anyway, seems like you cannot have it - but for those prices I would select another hosting company... they are really expensive and don't offer you standard stuff like php/mysql

---

### Post by hanzj on 2007-11-14
EndPerfform,
You asked who hosts our website. I gave you the wrong url. The correct url is [http://www.elhost.com/](http://www.elhost.com/).

---

