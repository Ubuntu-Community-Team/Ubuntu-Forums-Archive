---
title: "Synaptic error, no idea what to do"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by Lderan on 2007-11-20
The error is:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E:_ cache->open() failed , please report

I tried to use dpkg --configure -a, but it made me use sudo on it.
The problem with this is that nothing happening. It looks like its trying to download

This is what it looks like after I try it:
Resolving fpdownload.macromedia.com... 84.53.158.70
Connecting to fpdownload.macromedia.com|84.53.158.70|:80... 

It justs remains like that, it is more then likely my connection as I am living at uni and theres a bunch of restrictions on network use.

Any ideas welcome!

---

### Post by Mazza558 on 2007-11-20
Looks like a sources problem.. do you have any third-party repositories enabled?

---

### Post by Lderan on 2007-11-20
I don't think I have

---

### Post by rsambuca on 2007-11-20
First  enter this in a terminal

sudo dpkg --configure -a

---

### Post by Lderan on 2007-11-20
> **Lderan said:**
> 
This is what it looks like after I try it:
Resolving fpdownload.macromedia.com... 84.53.158.70
Connecting to fpdownload.macromedia.com|84.53.158.70|:80... 

It justs remains like that, it is more then likely my connection as I am living at uni and theres a bunch of restrictions on network use.


I have tried it

I just tried to install a debian package and an error has come up saying "broken dependencies"
how on earth do i fix that x.x

---

### Post by billgoldberg on 2008-01-06
> **rsambuca said:**
> First  enter this in a terminal

sudo dpkg --configure -a

Thanks that did the trick.

---

