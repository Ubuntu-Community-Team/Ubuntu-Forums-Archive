---
title: "Checking if SSH is Installed"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by drndrw on 2007-11-19
Hi. I just installed Ubuntu server 7.10 on my machine, and I'm not sure if I installed SSH or not during the setup. How can I check? Thanks.

---

### Post by mellowd on 2007-11-19
open up a terminal and type this:

```
apt-get install openssh
```

if it isn't installed it will, if it already is it'll tell you.

---

### Post by coolguy2006delhi on 2007-11-19
open up terminal and type this 

> which ssh

If you get the path of ssh , it is installed !

---

### Post by Inxsible on 2007-11-19
> **coolguy2006delhi said:**
> open up terminal and type this 



If you get the path of ssh , it is installed ! + 1 on that.

infact you can use the which command to check just about anything that you have installed. I think the locate command also does the trick.

---

### Post by drndrw on 2007-11-19
I got /usr/bin/ssh. Does that mean it's installed? Thanks. But I also tried locate and it said no such file or directory.

---

### Post by taurus on 2007-11-19
Do you want to connect to another machine or do you want another connected to yours?

---

### Post by mivo on 2007-11-19
Just type ssh. :) If it is there and can be found, it will give you a list of options. If not, you will get an error message. And yes, seems to already there. The Ubuntu CDs install the SSH client. The server needs to be installed separately (only do that if you really need it and know how to make it secure, i.e. no external root access).

---

### Post by mellowd on 2007-11-19
That means you got it

---

### Post by kefurd06 on 2007-11-19
yes, just type ssh in the bash. if u have it, u'll get parameters for it. if not, u'll get an install notification.

> open up a terminal and type this:

Code:

apt-get install openssh

if it isn't installed it will, if it already is it'll tell you.

this sort of works. but if u don't have the latest version, u get an install offer. (even though u have A version).

---

### Post by schorsch on 2007-11-19
```
dpkg -l|grep ssh
```

---

### Post by drndrw on 2007-11-19
Okay. I typed SSH and I got a list of commands. I guess it works. Thanks!

---

