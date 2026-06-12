---
title: "How to edit Modules.conf"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by djw on 2006-07-08
Hi guys I'm trying to edit modules.conf so I can try and get my plantronics DSP 500 working.  However I can't because the file is read only on my account and I can't get into the /root account through the login screen.  I must be missing something.

---

### Post by scxtt on 2006-07-08
if it's your box, do **sudo vi /etc/modules.conf** from a terminal -- you'll just enter your password (assuming your were the 1st account on the box) ...

if you don't like vi, do **gksudo gedit /etc/modules.conf** from the command line ...

---

### Post by Apple 101 on 2006-07-08
Does this get autoloaded on bootup?  Because I don't have such a file.  I used /etc/modules.

---

### Post by scxtt on 2006-07-08
yeah, i don't either - i used /etc/modules to load my sensor module at boot ...

---

### Post by djw on 2006-07-08
That is what I ment.  I changed it now thanks for the help.

---

