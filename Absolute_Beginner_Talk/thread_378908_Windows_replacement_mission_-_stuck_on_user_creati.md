---
title: "Windows replacement mission - stuck on user creation"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by simonb_sgp on 2007-03-07
Howdy!

I am trying to replace some Windows servers with Ubuntu 6.10 server. The installation went OK, I've added a port to the SpikeSource stack and ALM Suite 0.7 (both from [www.headwestsoftware.com](www.headwestsoftware.com)) for change and config management. All is working except I can't create new users.

Using adduser or useradd creates a new directory in /home with the skeleton contents copied OK. /etc/passwd shows the new user name, but the format is different:

myuser_name:x:1000:1000:myuser_name,,,:/home/myuser_name:.bin/bash

verses

newuser:x:10001:1001::/home/newuser:/bin/sh

adduser does not ask for a password and does not exit with a result code...

Needless to say i can't login as newuser.

I am totally new to all forms of Unix, so please be verbose in your assistance.

Thank you in advance.

Simon.

---

### Post by vayde on 2007-03-08
You need the 'passwd' command.

As root type 'passwd <username>'.  That will let you set the password.

further info type 'man passwd'.

Man pages are a pain in the neck to read at first, but they are well worth getting used to.  All the answers are in there, you just have to get used to reading the format.

good luck.

---

### Post by simonb_sgp on 2007-03-08
**Thanks!**

not only did that work, but having restarted for 'other' reasons, adduser and useradd now both present the correct output and prompts for additional info.

Cheers.

Simon.

---

