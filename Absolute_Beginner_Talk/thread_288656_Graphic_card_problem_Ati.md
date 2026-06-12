---
title: "Graphic card problem: Ati"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by dysko on 2006-10-30
Just wanted to ask could someone help me and tell me how to install or where to begin with search for solution of my problem.

I have ASUS A9Rp laptop wich uses graphic card **Ati Xpress 200M 128Meg**, but OS *(Kbuntu 6.06) does not recognize it. Should upgrade on Edgy help me?


Please help.

---

### Post by pay on 2006-10-30
Try this guide to get your drivers working.
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
Make sure that you have your /etc/X11/xorg.conf properly setup

An upgrade to xorg 7.1 (with edgy) will most likely break your drivers and require you to reinstall them.

---

### Post by Circus-Killer on 2006-10-30
dont know if fglrx driver supports your ati card, but fglrx is what you need for most ati cards. follow the instructions here:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

if you stick with dapper, you can ignore the part about disabling composite. hope you have better luck.

---

### Post by adam.tropics on 2006-10-30
Yes the fglrx driver from ATI supports it, at least mine runs fine. It also runs, though less well, with ati or radeon.

---

### Post by rlozano on 2006-10-30
fglrx driver supports your X200, but you have to make sure the you will use the 8.28xxx driver since itt not supported in 8.29.xxx

hope this helps..

---

### Post by Circus-Killer on 2006-10-30
> **adam.tropics said:**
> Yes the fglrx driver from ATI supports it, at least mine runs fine. It also runs, though less well, with ati or radeon.

just for the people who dont know, that is because the fglrx driver is closed-source driver written by ATI themselves, whereas the ati and radeon driver are open-source and not written by ati.

obviously the ati proprietary driver has the best support for its hardware.

---

### Post by adam.tropics on 2006-10-30
> **rlozano said:**
> fglrx driver supports your X200, but you have to make sure the you will use the 8.28xxx driver since itt not supported in 8.29.xxx

hope this helps..

Well again, it does for me.

[Read it from here too,]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.29.6.html")

---

### Post by dysko on 2006-10-31
Tnx boys,,,, it was helpfull

---

