---
title: "How do I change my kernel?"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-02-04
Hey, right now I'm using dapper with kernel 2.6.15-27-386, and I was wondering if there was a way to update my kernel to 2.6.17-rc2?


:D

---

### Post by dcstar on 2007-02-04
> **kbsuperstar said:**
> Hey, right now I'm using dapper with kernel 2.6.15-27-386, and I was wondering if there was a way to update my kernel to 2.6.17-rc2?


:D

All official kernel builds will be available via Synaptic, if you want to build your own kernel there are detailed HOWTOs in the "Tips" section of this forum.

---

### Post by kbsuperstar on 2007-02-04
Thanks, but...

I can only find one kernel build in synaptic (2.4.27) ... any way to get newer builds?

---

### Post by amohanty on 2007-02-04
Look for generic names like linux-image-generic. Its not actually a package, but a  dummy package that depends on the latest kernel. That way at next update you will get the latest.

HOWEVER dapper is the LTS version so that will probably not have the regular updates you say with breezty and edgy.

HTH
AM

---

### Post by kbsuperstar on 2007-02-04
All the images are only 2.5.xx still in synaptic... but thakns. I'll try kernel.org

---

### Post by kbsuperstar on 2007-02-04
Ok, I'm confused. I guess I'm trying to patch my kernel to 2.6.20, and it  (the HOWTO) says just to ask the Ubuntu Team.

It also says to do "sudo apt-get install linux-tree" but I just get an error 

```
kyle@kyle-laptop:~$ sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-tree

```

So... how would I patch my kernel? Or is there a howto for this?? Because I only find ones about setting up a new kernel from scratch (or so it would appear)

:D Thanks :D

---

### Post by amohanty on 2007-02-04
Ok, first off kernel patching should be last thing you want to do if you just started using linux. So why exactly do you want to upgrade your kernel?

Its a lot of work and lots of things can go wrong, so unless some critical peice of hardware is not working or this is a test system you are using to learn linux, I would strongly advise against it.

the linux source tree packege is called: kernel-tree-xyzw

also you might need the linux-kernel-headers and linux-kernel-devel pkgs.

HTH
AM

---

### Post by kbsuperstar on 2007-02-04
Only new kernels past 2.6.17-rc2 have BCM43xx driver installed + working ... :D

---

### Post by shareMenaPeace on 2007-02-04
> **kbsuperstar said:**
> Only new kernels past 2.6.17-rc2 have BCM43xx driver installed + working ... :D

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

maybe the driver download
[ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/winxp64bit/80211g.zip)

---

### Post by amohanty on 2007-02-04
Well best of luck to you then. 

Is this  a wireless card or something? I am sorry I dont recognize the hardware name.

AM

---

### Post by kbsuperstar on 2007-02-04
Yeah, it's a wireless card (broadcom chipset). How do I install this driver??

---

### Post by shareMenaPeace on 2007-02-04
Depending on which ubuntu you use - checkout

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by kbsuperstar on 2007-02-04
> 1.3.2.1. Extract it Yourself

If/when Ubuntu do a kernel upgrade to 2.6.17 or later you MUST use wl_apsta.o (the script does that). The new module does not have the invalid AP bug. To obtain the wl_apsta.o visit [WWW] [http://drinus.net/airport/wl_apsta.o](http://drinus.net/airport/wl_apsta.o). (From the bcm43xx team). The latest firmware package contains this driver. 

Once I get to this part of the tutorial, I download wl_apsta.o, but I can't seem to execute the script. I try double-clicking in nautilus and typing the filename in the terminal, I just get an error...


Help?

---

### Post by beathan on 2007-02-04
What sort of error are you getting?

You may need to open a terminal window and make the script executable:

```
chmod +x <scriptname here>
```

---

### Post by Cippy on 2007-02-05
> **amohanty said:**
> Ok, first off kernel patching should be last thing you want to do if you just started using linux. So why exactly do you want to upgrade your kernel?

Its a lot of work and lots of things can go wrong, so unless some critical peice of hardware is not working or this is a test system you are using to learn linux, I would strongly advise against it.

the linux source tree packege is called: kernel-tree-xyzw

also you might need the linux-kernel-headers and linux-kernel-devel pkgs.

HTH
AM

I'm looking to patch my kernel from 2.6.17-10 to 2.6.18 because it has the ZD1211 driver I need already implemented (I can't implement it myself for my life). Bad idea?

---

### Post by amohanty on 2007-02-06
As I said, if you are ok with a possibly borked system, until you can fix it, go ahead :) Not trying to scare you, but although its become a lot easier than it used to be rebuilding the kernel is not a good idea for your primary system. Also everytime the kernel is upgraded, you have to repeat the process, unless of course you have LTS and you can rest easy for some time. Theres a reason (among others) debian releases are so long (as opposed to ubuntu).

The easiest option would be to pick up a cheapo trendnet (~20) off of newegg, I got two cos my godamn thinkpad t60's intel wlan chip just refuses to work and and older laptop does not have wireless built in. It works great and easily with ndiswrapper, and is just something handy to keep around if you use laptops.

HTH
AM

---

