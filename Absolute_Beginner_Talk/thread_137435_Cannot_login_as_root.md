---
title: "Cannot login as root"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by n11 on 2006-02-27
Cannot login as root. At the login  screen I typed the username as "root" and tried all passwords from "root","ubuntu" to the password of my user account. I have to edit xorg.conf to fix a display problem and I understand I cannot do that until I am logged on as root. I also tried "recover mode" but I cannot open the file and the message says that the file does not exist. (Actually it said the /etc directory also did not exist). Please help.
Thank you.

---

### Post by aysiu on 2006-02-27
Read these two links:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/linux/permissions](http://www.psychocats.net/linux/permissions)

---

### Post by benplaut on 2006-02-28
read the docs above, but to sum it up, the command that you need is:

gksudo gedit /etc/X11/xorg.conf

when it asks for a password, it wants *yours*

---

