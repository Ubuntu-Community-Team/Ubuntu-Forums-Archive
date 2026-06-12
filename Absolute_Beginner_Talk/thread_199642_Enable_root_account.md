---
title: "Enable root account?"
date: 2006-06-19
forum: Absolute Beginner Talk
---

### Post by n00b@linux on 2006-06-19
Hi
 
I am new to Ubuntu.
 
I have heard so much good press about Ubuntu recently that I decided to give it a try.  I downloaded 6.06 (Dapper) last night and installed it on my Thinkpad T40.
 
Installation went without a hitch.  This morning I downloaded a .mp3 file to /home but had a problem when I tried to move it over to my (USB) iRiver player.  I had a message saying I did have admin status to do it.  Normally, I would get around such a problem by going into Terminal and typing 'su'.
 
I did this and it asked me for my password.  Here's the rub:  when I installed Ubuntu I can only remember typing in one password - for the user/client account.  I cannot recall ever being prompted to create a password for the root/admin account.  I tried all sorts of passwords for root, but none worked.
 
I read something on this forum about enabling the root account.  I searched the forum for 'enable root' but didn't see anything.  I couldn't find anything in the desktop user manual eithers.
 
Please, can someone explain to me how the root/user dichotomy works on Ubuntu and what I need to do to get root privileges?
 
Thx

---

### Post by upendran on 2006-06-19
Try 'sudo -i'. Password? - use your login password! That is the only one you will ever need.

---

### Post by n00b@linux on 2006-06-19
Thanks!  That's a very different way of working compared to SuSE (which is where I've come from distro-wise).
 
btw, for anyone reading this post, I subsequently found the entry in the desktop user guide:
 
[http://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html#root-and-sudo]("http://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html#root-and-sudo")
 
I guess this is typical with n00bs like me.

---

### Post by Gustav on 2006-06-19
Read this for an explanation:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

