---
title: "Fresh 7.04 can't compile &quot;Hello World&quot;?"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by racarate on 2007-05-16
I just installed Ubuntu for the first time, and I tried to run my own "Hello World".  The compiler complained that crt1.o could not be found.

I don't understand what's going on here -- isn't the C runtime needed for _any_ program to compile?

I've never delved into the workings of gcc before, so I'm not sure where this file is supposed to go, or where I can find it.

Any help would be appreciated.


-Nick

---

### Post by lloyd_b on 2007-05-16
First step - In a terminal window:
```
sudo apt-get build-essential
```
(or install the "build-essential" package via Syntaptic/Adept).

This should guarantee that you have a complete build system installed.

Then try the compile again.

Lloyd B.

---

### Post by jtraub on 2007-05-16
```

mikv@condor:~$ sudo dpkg -S crt1.o
Password:
libc6-dev: /usr/lib/Scrt1.o
libc6-dev: /usr/lib/Mcrt1.o
libc6-dev: /usr/lib/gcrt1.o
libc6-dev: /usr/lib/crt1.o

```

This means you should install libc6-dev package.
But, probably, installing build-essential is better (This package contains tools and libraries for basic development).

---

### Post by taurus on 2007-05-17
> **lloyd_b said:**
> First step - In a terminal window:
```
sudo apt-get build-essential
```


```
sudo apt-get update
sudo apt-get **install** build-essential
```

---

### Post by racarate on 2007-05-17
Ok, I managed to install libc6-dev using apt-get.

Apt-get kept giving me inane 'no such package' messages until I realizes I had to execute the command 'apt-get update' before anything would work.  D'oh!

I have one more small question -- 'apt-get install cscope' doesn't work.  Is this package not supported by Ubuntu?

---

### Post by racarate on 2007-05-17
Hey, that 

dkpg -S <file that's missing>

trick is awesome!  Thanks!!!

---

### Post by hyper_ch on 2007-05-17
You could install: apt-file
With that you can look in what package a certain file is

sudo apt-get install apt-file
sudo apt-file update

---

