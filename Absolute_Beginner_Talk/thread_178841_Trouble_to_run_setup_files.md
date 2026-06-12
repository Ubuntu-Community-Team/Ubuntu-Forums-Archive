---
title: "Trouble to run setup files"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by Sigurd on 2006-05-18
Im actually new to linux today so I need some help.
I tried to download amsn, but when im trying to open the setup file, I just get the message that you cant run that. This also happend when I tried to install some other programs.
Do I need to download something so I can download these programs?

---

### Post by aysiu on 2006-05-18
You probably need to read these two links:
[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Otherwise, if you want the latest aMSN (instead of the one in the repositories), use [this script](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47).

---

### Post by Klaidas on 2006-05-18
Also, this link: [http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF](http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF)
Hope this helps :)

---

### Post by aysiu on 2006-05-18
[QUOTE=Klaidas]Also, this link: [http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF](http://www.linux.org/lessons/interm/c191.html#INSTALL-STUFF)
Hope this helps :)[/QUOTE] That's a very good overview for general Linux distributions, but if you use the Debian-based instructions, you'll just get an error message saying that *apt-get* or *dpkg* needs to be executed as root.

---

### Post by S{yndrom}e on 2006-05-18
if the error message you are getting has something to do with "Access denied; you do not have permissions" then you can do this

chmod +x *thefullfilename.extention*

---

### Post by Klaidas on 2006-05-18
Aysiu: true.
But it's just needed to add "sudo" before the command and it works :)
My mistake, I didn't point to root on ubuntu. Sorry for that.
Here it is: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

