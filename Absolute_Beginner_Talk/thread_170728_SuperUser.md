---
title: "SuperUser"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Nekkron on 2006-05-05
Is there any way to re-create the su password? I tried any password I could think of me ever using and it has denied them all. 

And yes, I did check the spelling. I just want to know if I can either change the su password or if i can find out what it is.

---

### Post by Sef on 2006-05-05
Root is closed by default.  Sudo is what is used when root is needed.   This is much safer than root.  Read this wiki.

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by Nekkron on 2006-05-05
so how would my command line look if i were trying to install ATI drivers?

ATI says use this command:
sh ./ati-driver-installer-8.24.8-i386.run

but when i do that it tells me i need to be su

---

### Post by Sef on 2006-05-05
Read this on article on how to install Shell scripts. (About 2/3 of the way down.)

[http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal]("http://monkeyblog.org/ubuntu/installing.html#navigating_the_terminal")

---

### Post by hw-tph on 2006-05-05
[QUOTE=Nekkron]so how would my command line look if i were trying to install ATI drivers?

ATI says use this command:
sh ./ati-driver-installer-8.24.8-i386.run

but when i do that it tells me i need to be su[/QUOTE]

**sudo -i** will give you a root terminal. Even the environment variables that are checked by most installers will change, allowing most installers to recognize you're running as root.


Håkan

---

