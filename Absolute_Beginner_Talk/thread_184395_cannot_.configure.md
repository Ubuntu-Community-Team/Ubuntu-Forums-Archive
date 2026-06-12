---
title: "cannot ./configure"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by knewmocker on 2006-05-29
I had downloaded a program and I had to ./configure it and all I had gotten was

checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I was trying to download gcc but if I dont have a compiler I cant even install that, and I dont see in my program list any compilers that I see. can anyone help me

---

### Post by Sutekh on 2006-05-29
Install the GNU C Compiler (gcc) and build-essential tools using apt-get.  These packages are pre-built, you don't have to do it yourself
```
sudo apt-get install build-essential gcc
```

---

### Post by knewmocker on 2006-05-29
wow that was so easy. I had tried all day to install gcc and I thought I was never going to get it

---

### Post by Sutekh on 2006-05-29
Cool glad you got it fixed.  Although I often wonder how to the makers of gcc compile it?  Can it compile itself? :-k

Installing by apt-get or Synaptic really is the way to.

These links have some more good info on installing software

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)

[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by aysiu on 2006-05-29
Just to break it down a little: [QUOTE=Sutekh]
These links have some more good info on installing software

[http://psychocats.net/ubuntu/installingsoftware.php](http://psychocats.net/ubuntu/installingsoftware.php)[/quote] Quick overview--explained in text. It applies to Ubuntu, Xubuntu, and Kubuntu.

> 
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/) Very detailed and long with screenshots and explanations. Focused on Ubuntu for now, and mentions some features that are available only in Dapper.

I would recommend reading *both*.

---

