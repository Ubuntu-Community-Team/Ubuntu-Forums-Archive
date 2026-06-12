---
title: "Help installing eyetoy."
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by lopagof on 2007-05-01
I currently use xubuntu 6.06 and really need help with installing eyetoy drivers.

I looked up a forum here [http://ubuntuforums.org/showthread.php?t=272328](http://ubuntuforums.org/showthread.php?t=272328) and it worked up to a point.

i got up to ```
sudo insmod /lib/modules/`uname -r`/extra/ov51x.ko
``` and then it said it could not find the directory I know i did something wrong but could someone with more ubuntu experiance help me please.

thanks everyone.:KS

---

### Post by compiledkernel on 2007-05-01
what does a 

uname -r 

tell you in a terminal.

---

### Post by lopagof on 2007-05-01
what do you mean by that?

`uname -r` is my kernel version

---

### Post by lopagof on 2007-05-01
2.6.17.0-generic or something like that

---

### Post by compiledkernel on 2007-05-01
can you cd to that directory? 

cd /lib/modules/`uname -r`/extra/

and if not, what kernel versions are actually listed in /lib/modules/

---

### Post by lopagof on 2007-05-01
yes i can cd without sudo as I am using root

and 2.6.17 is my kernel version

---

### Post by lopagof on 2007-05-01
any other help:confused:

---

