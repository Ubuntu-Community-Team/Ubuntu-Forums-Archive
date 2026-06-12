---
title: "Mail Server setup"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by GADO on 2006-07-22
I don't know if this is the right place to ask, but hopefully someone will be able to help or point me in the right direction!!

I have just installed Ubuntu Server 6.06. I have a small project where I need to set up an email server, as well as a website to login and check the email. 

I've already installed Apache2 which is only a smart part of this, and I have little to no clue as to what to install for the email server and continue from there. 

Any help is greatly appreciated!!

---

### Post by ProjectGod on 2006-07-22
**openXchange**. its the MS exchange equivalent. so they say anyway. i havent tried to configure this myself. would like to but not much time.

please let us know how you go! we very interested :D

---

### Post by GADO on 2006-07-23
Hi,

I haven't had much success getting openXchange to work... so I installed postfix which has allowed me to send mail. However am I right in assuming I can't retrieve email with this application?

I was thinking about dovecot but I'm unfamiliar with it. My end goal is to be able to not only send and receive email, but be able to login to a mail account from a web page and check email through the web interface.

If anyone has worked with something like this please offer up any advice you feel relevant as I would greatly appreciate it.

Thanks again to all who reply,
Jason

---

### Post by ubuntu-geek on 2006-07-23
This might help get you going in the right direction..

[http://howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu](http://howtoforge.com/postfix_antispam_mailscanner_clamav_ubuntu)

---

