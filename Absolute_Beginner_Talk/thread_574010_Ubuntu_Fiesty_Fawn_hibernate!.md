---
title: "Ubuntu Fiesty Fawn hibernate!"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by khurrum1990 on 2007-10-12
Hi, I need some help configuring hibernate.
I currently dual boot OPensuse 10.2 and ubuntu 7.04.
I set up hibernate to work in opensuse 10.2 doing the following:
I blacklisted the sis_agp module and in my xorg.conf I added the line Option NvAGP  3. I tried doing the same for Ubuntu but it didn't work. So I looked at the driver version both drivers are from their repositoroes and I noticed that the Opensuse drivers are the latest which are 100.14.19 wehere as the Ubuntu drivers are 1.0.something so they r pretty old. Could this be the problem, I mean does the driver version matter? Please help or give any ideas u can think of.
Take care!

---

### Post by klytu on 2007-10-14
Make sure that you have enough swap space for your Ubuntu installation.  I built a new computer with 2GB of RAM and I couldn't get hibernation to work for it until I set up a swap partition of 2GB for Ubuntu. If you have a lot of RAM, Ubuntu sets up minimal swap partition by default and this will not be enough to use hibernation.

---

