---
title: "How do I install Oracle Database 10g Express on powerpc in ubuntu lucid?"
date: 2010-10-25
forum: Apple Hardware Users
---

### Post by Rgibbons on 2010-10-25
I have downloaded three different files from the Oracle site:

oracle-xe_10.2.0.1-1.0_i386.deb

oracle-xe-10.2.0.1-1.0.i386.rpm
and
oracle-xe-univ-10.2.0.1-1.0.i386.rpm

I was assuming from what I read that I was supposed to use the second version.

I am a beginner, so I was using the terminal and followed Oracle's instructions on installation.

1. login to root

2.I tried each file using their prescribed directions and got the follow errors:

root@powerbook:~# rpm -ivh oracle-xe-10.2.0.1-1.0.i386.rpm
No command 'rpm' found, did you mean:
 Command 'rm' from package 'safe-rm' (universe)
 Command 'rpl' from package 'rpl' (universe)
rpm: command not found


root@powerbook:/home/rodney/Downloads# sudo dpkg -i oracle-xe_10.2.0.1-1.0_i386.deb
dpkg: error processing oracle-xe_10.2.0.1-1.0_i386.deb (--install):
 package architecture (i386) does not match system (powerpc)
Errors were encountered while processing:
 oracle-xe_10.2.0.1-1.0_i386.deb


anyone know what I am doing wrong?

---

### Post by linuxopjemac on 2010-10-26
oh yes, you are trying to install an Intel based build. That will never work on PPC.

---

### Post by Rgibbons on 2010-10-26
Is there such a thing as a powerpc based build?

---

### Post by linuxopjemac on 2010-10-26
I am afraid there is none:
[http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html](http://www.oracle.com/technetwork/database/express-edition/downloads/102xelinsoft-102048.html)

---

### Post by Rgibbons on 2010-10-26
I installed a Debian package builder available through Ubuntu. It says it is supposed to work on several different platforms. I haven't tried it yet, but I wonder if the Debian version of Oracle Express will work.

---

### Post by tehnad on 2010-11-11
Please let us know if it does . . .

---

