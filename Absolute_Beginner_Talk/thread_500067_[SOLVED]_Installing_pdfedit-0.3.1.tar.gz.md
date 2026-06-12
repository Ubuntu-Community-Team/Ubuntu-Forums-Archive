---
title: "[SOLVED] Installing pdfedit-0.3.1.tar.gz"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by jmfa59 on 2007-07-13
When trying to install pdfedit-0.3.1.tar.gz the instruction says that I have to compile it when I used ./configure this the message I got _QTDIR environment variable must be se_t of course I couldn't do sudo make install any Idea.
THANKS

---

### Post by twiceasworn on 2007-07-13
Could you post the error you get when compiling in it's entirety?

---

### Post by aysiu on 2007-07-13
Maybe this might help?
[https://help.ubuntu.com/community/PDFedit](https://help.ubuntu.com/community/PDFedit)

---

### Post by jmfa59 on 2007-07-13
This the error I got as normal user and su
jasem@ubuntu:~/Desktop/pdfedit-0.3.1$ ./configure
configure: error: QTDIR environment variable must be set
jasem@ubuntu:~/Desktop/pdfedit-0.3.1$ sudo su
Password:
root@ubuntu:/home/jasem/Desktop/pdfedit-0.3.1# ./configure
configure: error: QTDIR environment variable must be set
root@ubuntu:/home/jasem/Desktop/pdfedit-0.3.1#

---

### Post by twiceasworn on 2007-07-13
From what I am able to find out just putting the error in google is that you need to find out where your qt-libs are and then export that path so the progam knows where to look.  I found this from this [page]("http://www.smcc.demon.nl/camstream/troubleshooting.html").  It is for a different progam but it is addressing the exact same issue you are having.

---

### Post by aysiu on 2007-07-13
Any reason in particular you want to compile from source instead of using the .rpm or .deb, as described in the link I posted earlier?

---

### Post by twiceasworn on 2007-07-13
> **aysiu said:**
> Any reason in particular you want to compile from source instead of using the .rpm or .deb, as described in the link I posted earlier?

Heh, I didn't even think to ask that.  Yes, why are you compiling?

---

### Post by jmfa59 on 2007-07-13
Why I am compiing is very simple because the instruction say that, I didn't know any other way untill I read the first post of AYSIU after looking at the link I did it so thanks alot guys your are great
THANKS

---

