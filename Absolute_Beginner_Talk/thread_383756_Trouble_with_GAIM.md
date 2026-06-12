---
title: "Trouble with GAIM"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by raccoonone on 2007-03-13
I'm trying to connect to AIM from Ubuntu, but I couldn't get AIM to install from aim.com I tried to use GAIM which comes with Ubuntu, but after I enter my username and password I get an error that they are invalid. I've retyped them many times, and I'm sure they're right.

I noticed though that the version of GAIM that I have is Beta3, and the newest on their website is Beta6. How do I update to the newest version? Synaptic doesn't seem to have the new one listed.

---

### Post by bollix47 on 2007-03-13
[http://repository.debuntu.org/](http://repository.debuntu.org/)

---

### Post by raccoonone on 2007-03-13
Thanks, I got GAIM updated, but I'm still having problems logging into AIM. Are there any settings that I need to configure?

---

### Post by bollix47 on 2007-03-13
Try going [_here_]("https://my.screenname.aol.com/_cqr/login/login.psp?mcState=initialized&sitedomain=my.screenname.aol.com&lang=en&locale=us&authLev=2") and signing in to make sure you're using the correct information.

---

### Post by raccoonone on 2007-03-13
Yep, it works just fine. I can check my email, and I can even log in with their AIM Express. But I can't login through GAIM. I even tried turning cap-locks on and off to see if that was the problem.

---

### Post by bollix47 on 2007-03-13
AIM and Gaim working fine here so not sure what to tell you.  When you open Gaim is your AIM account listed under accounts?

On the advanced tab I have:

server = login.oscar.aol.com
port = 5190

Is it possible you're somehow blocking this port?

Also, are you using any kind of proxy?

---

### Post by bollix47 on 2007-03-13
Is your password longer than 8 characters?  

A fairly [_old post_]("https://sourceforge.net/forum/message.php?msg_id=3364429") on the Gaim forum suggests that was a problem at one point.

---

### Post by raccoonone on 2007-03-13
Yep, that was the problem. Thanks a ton!!! My password is 10 characters. That's pretty weird that you can login without supplying the full password. Seems like a bit of a security flaw in AOL's programming to me.

---

