---
title: "Can I ever compile? Checking for X: Problem."
date: 2006-06-14
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-06-14
I am repeatedly failing at compiling the source of most programs at this point:-


./configure

> 
Checkin for X:.. configure: Error : can't find X Includes. Please check your installation and add the correct paths.



Please help solve this issue.

Thanks in advance.

---

### Post by dabang on 2006-06-14
You have to install the x-development files. As I don't have my Ubuntu box right now, I can't tell you the precise names, but If you search via synaptic, look for something like xorg-dev or xserver-dev. Basically have a look at all the X-dev packages. Sorry for the lack of details...

---

### Post by halfvolle melk on 2006-06-14
```
sudo apt-get install build-essential
```
should let you build most common things.

---

### Post by vinodis on 2006-06-14
ok. thanks many. i found a similar [thread]("http://www.ubuntuforums.org/showthread.php?t=23570&highlight=X-dev") too.

---

