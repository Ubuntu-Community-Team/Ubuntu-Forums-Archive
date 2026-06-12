---
title: "ubuntu 7.10+pentium2=?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by exandas on 2008-03-15
I`ll try to install ubuntu 7.10 in one dell latitude with intel pentium 2  266mhz
system memory 64mb.May i or i must find something else .
thanks

---

### Post by PurposeOfReason on 2008-03-15
For something that old you'll need DSL or puppy linux.

---

### Post by freebios on 2008-03-15
an older ubuntu distro should work fine.  the reason I recommend ubuntu is because it has great hardward compatibility in comparison to other distros.  Also what the minimum recommendations for Ubuntu are just guidelines.  Obviously it will run slow, but with minor tinkering I think it will work for you because I have ran it on a 300 mhz, 3 gig harddisk, with 128 megs ram just fine. (note I didn't run 7.10)  if you chose an older distro you should be OK because they require less powerful hardware. good luck

---

### Post by sandysandy on 2008-03-15
64 mb RAM is too less. can u upgrade the RAM.

 here is what ubuntu website has to say about System Requirements

>  Ubuntu is available for PC, 64-Bit and Mac architectures. At least 256 MB of RAM is required to run the desktop install CD. Install requires at least 4 GB of disk space. 



regards

---

### Post by forrestcupp on 2008-03-15
Maybe Xubuntu would work for you.

---

### Post by PurposeOfReason on 2008-03-15
> **forrestcupp said:**
> Maybe Xubuntu would work for you.
```
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.
```

Nope. If anything this is a DSL, puppy linux, or arch + openbox machine.

---

### Post by forrestcupp on 2008-03-15
> **PurposeOfReason said:**
> ```
Minimum system requirements

To run the Desktop CD (LiveCD + Install CD), you need 128 MB RAM to run or 192 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM.

To install Xubuntu, you need 1.5 GB of free space on your hard disk.

Once installed, Xubuntu can run with 192 MB RAM, but it is strongly recommended to have at least 256 MB RAM.
```

Nope. If anything this is a DSL, puppy linux, or arch + openbox machine.

Wow!  A computer that can't even run Xubuntu.

---

### Post by PurposeOfReason on 2008-03-15
> **forrestcupp said:**
> Wow!  A computer that can't even run Xubuntu.
All Xubuntu is is Ubuntu with XFCE instead of Gnome. It isn't **that** much lighter. Ubuntu is rather bloated and patched. For many instances this is good, for older machines, not so much.

---

### Post by Bölvaður on 2008-03-15
Puppy is the thing for you mate :)

---

### Post by dptxp on 2008-03-15
Even Puppy will not run unless you make a swap partition (512MB-1GB) first, Puppy needs 128 MB RAM. For 64 MB RAM you need SWAP first. Use GParted to create SWAP.

You can also check Anti-X.

DSL should run. Check Feather Linux too.

---

### Post by CREEPING DEATH on 2008-03-15
I have Debian on a Pentium-MMX 233 Mhz machine wth 64 MB RAM, using XFCE.  It isn't the fastest, but it does work.  Go to [www.debian.org](www.debian.org) and download the XFCE CD and try that.  Just don't expect speed!

CD

---

### Post by sandysandy on 2008-03-15
have a look at this link on various linux distros

[http://distrowatch.com/](http://distrowatch.com/)

regards

---

### Post by schiznik on 2008-03-15
> **CREEPING DEATH said:**
> I have Debian on a Pentium-MMX 233 Mhz machine wth 64 MB RAM, using XFCE.  It isn't the fastest, but it does work.  Go to [www.debian.org](www.debian.org) and download the XFCE CD and try that.  Just don't expect speed!

CD

I second debian for a box like that, however I would just install the base system (ie the base for ubuntu-minimal), that leaves you with linux,bash,apt/dpkg and not alot else :). From there you can install just the packages that you need, rather than whole groups (to keep space/ram/cpu usage to a minimum), and go with one of the *box window managers instead of a desktop environment.

It might take some work getting a desktop up and running, but it will be worth the effort in the end.

If you have a faster linux box available over the LAN, you may want to look into the remote features of X, that you let you use the more powerful box to run the application and just display it on the older box. I used to do this with a p75 a few years ago, it was still slow, but faster than trying to run firefox for example locally.

---

