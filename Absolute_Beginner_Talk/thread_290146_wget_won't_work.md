---
title: "wget won't work"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by razo559 on 2006-10-31
ok i dont know what wget means but every time i try to install something and it asks me to first install through wget [http://.](http://.)..... and i always get an error

can anyone help

---

### Post by TigerCR1200 on 2006-10-31
We are going to need a little more help than this inorder to help you.

What exactly does it say when you try a wget command?

---

### Post by po0f on 2006-10-31
razo559,

What is the error?  Cannot connect to host?  File not found (404)?  We need more information to diagnose your problem.

---

### Post by lapsey on 2006-10-31
> **razo559 said:**
> ok i dont know what wget means but every time i try to install something and it asks me to first install through wget [http://.](http://.)..... and i always get an error

can anyone help

to install wget: `sudo apt-get install wget`

wget is just a command to tell ubuntu to grab a file from the internet

so `wget http://support.dell.com/support/edocs/systems/dim2350/specs.htm`

grabs that file. the path must be correct for this to work.

---

### Post by FilipeRegis on 2006-10-31
wget is a program that open a http connection to a server, and retrieves a file, passed as parameter.
Ex: I want to download [http://www.internet.com/file.tar.gz](http://www.internet.com/file.tar.gz), then I use at the terminal: wget [http://www.internet.com/file.tar.gz](http://www.internet.com/file.tar.gz)

Perhaps you are behind a firewall or a proxy, and need to configure internet connection. Test if your conectivity is ok.

If this doesn't helps, I can't do anymore for you... *sorry*

---

### Post by FilipeRegis on 2006-10-31
isn't apt-get a frontend for wget?
I guess that if wget doesn't work, also apt-get will not.

---

