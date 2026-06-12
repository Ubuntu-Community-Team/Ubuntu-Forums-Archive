---
title: "Frsot wire"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by J0E0NE on 2006-06-07
After downloading frostwire for Ubuntu I was wondering why it wasn't working when i clicked on it in the applications menu, so i ran it in the terminal:
joe@ubuntu:~$ sudo /usr/bin/frostwire
Password:
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)

I know what that means but I have :The Sun Java Platform Standard Edition Runtime Environment (JRE) 5.0 installed

Is that not good enough?
If not what do I do?

Thanks in advance.

---

### Post by Rackerz on 2006-06-07
Install java again using this tutorial. 

[http://www.ubuntuforums.org/showthread.php?t=76702&highlight=installing+sun%27s+java](http://www.ubuntuforums.org/showthread.php?t=76702&highlight=installing+sun%27s+java)

---

### Post by J0E0NE on 2006-06-07
errr which java am I supposed to download?
There are a few differant ones, which does frost wire need?

thanks

---

### Post by Fornie on 2006-06-07
i got this from other thread...hope it helps

sudo update-alternatives --config java   >>> then select the java sun

---

### Post by J0E0NE on 2006-06-07
Afraid it didn't :(

---

### Post by Fornie on 2006-06-07
awww...

ei try this...i just followed the instructions on this link and it worked for me...

[http://www.ubuntuforums.org/showthread.php?t=148075](http://www.ubuntuforums.org/showthread.php?t=148075)

---

### Post by J0E0NE on 2006-06-07
=D> Ace! thanks that worked thanks alot :D

---

