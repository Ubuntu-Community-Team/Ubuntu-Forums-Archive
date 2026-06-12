---
title: "ACM Support?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Glass_Onion on 2006-06-16
Hey, I've tried installing moto4lin on Ubuntu Breezy and I can't use it right. I've tried looking around and using the wiki and figured out I'm missing some cdc-acm thing acording to [this](http://moto4lin.sourceforge.net/wiki/System_Configuration) page. I've tried looking around Synaptic and Google and am really struggling to get anything like it.

So my question is has anybody got moto4lin working? Or does anybody know where I can find this componant? I've been doing this on and off for a couple of days and I'm really getting frustrated so any help or suggestions are much apriciated. :)

---

### Post by Glass_Onion on 2006-06-16
*bump to front page*

---

### Post by trickyarcher on 2008-03-09
Onion,
I'm trying to get my Helio Heat phone to work in ubuntu.  I am in the process of prepping for installation of BitPim.  One of the pre-reqs is acm.  I installed it like so:

```

~$ sudo apt-get install acm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  acm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 730kB of archives.
After unpacking 1401kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com gutsy/universe acm 5.0-23.1 [730kB]
Fetched 730kB in 1s (607kB/s)
Selecting previously deselected package acm.
(Reading database ... 110978 files and directories currently installed.)
Unpacking acm (from .../archives/acm_5.0-23.1_i386.deb) ...
Setting up acm (5.0-23.1) ...

```

Hope this helps.  Afterward you should attach your device and see it in the Device Manager

---

