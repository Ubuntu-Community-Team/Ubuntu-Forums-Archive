---
title: "VNC start..."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-08-21
Im a Ubuntu noob, and some 'howto's" are to vague on how i can do this.

How can i make it so, VNC starts up during the initial boot up, BEFORE the login screen, so i can take control and perform the login and use my session? 

A very noob friendly instructions are welcome, thanks.

---

### Post by ddrichardson on 2007-08-21
Ideally the VNC server needs to be started before gdm, however I'm not sure if it can be run from a terminal:

[Explanation of how services are started.]("https://help.ubuntu.com/community/UbuntuBootupHowto")

[Debian Policy on Sysvinit]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit")

---

