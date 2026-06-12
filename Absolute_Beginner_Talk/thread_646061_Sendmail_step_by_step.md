---
title: "Sendmail step by step?"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Mramius on 2007-12-20
I've been googling and googling for some easy, step by step instructions on how to set up Mutt and sendmail.

I'm pouring over the man pages for these and looking at the config files for them both but can't really decipher them.

I can't find where I need to enter even the basic things like pop and smtp server information etc.

---

### Post by andrew.46 on 2007-12-22
Hi,

 Saw your post while searching up mutt material:

> **Mramius said:**
> I've been googling and googling for some easy, step by step instructions on how to set up Mutt and sendmail.

I'm pouring over the man pages for these and looking at the config files for them both but can't really decipher them.

I can't find where I need to enter even the basic things like pop and smtp server information etc.

Do you really need sendmail? If you are thinking of accessing your own isp or accessing something like gmail you really only need a program like ssmtp or msmtp.

Have a look at this Howto which will perhaps give you a general idea:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

or its big brother:

[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

 All the best,

    Andrew

---

### Post by albaz3245 on 2008-01-09
I'm having somehow a similar proplem -
I want to be able to send email betwenn my LAN machines only without internet connection by runing sendmail on each machine (no DNS, no Mail server)i.e just simply sending e-mail directly, but i failed. i succeeded to send e-mail locally, between several users of the same machine but not from one machine to another.Can someone help

---

### Post by rkd on 2008-01-10
I can't speak from my own experience, but I've seen it mentioned several times over the years that postfix is much easier to set up and use than sendmail is, and postfix has fewer security problems, too.

I don't know whether this is a Coke/Pepsi difference of taste or a real difference between the two, but if you are having trouble with sendmail, it might be worth a little investigation of postfix.

---

