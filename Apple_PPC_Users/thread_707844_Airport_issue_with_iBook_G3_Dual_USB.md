---
title: "Airport issue with iBook G3 Dual USB"
date: 2008-02-25
forum: Apple PPC Users
---

### Post by FruitSmack! on 2008-02-25
So this is my first foray into the world of Ubuntu and I've finally run into a snag no amount of playing with or searching for has been able to fix.

The Issue:
I have an iBook Dual USB (500mhz G3, 384MB RAM, 40GB HDD) that I installed a minimal command line only version of Ubuntu 7.04 on.  The wireless card worked fine after the initial install.  I then installed a few things (xorg, openbox, a few other cli progs).

Long story short, after finding out that the USB gamepad I use to play emulated games wouldn't detect correctly under the kernel I had (2.6.16-20), I did some research and used the directions on the PowerPCFaq to compile a new kernel for my iBook.

Everything seemed to work fine, but now I have no wireless.  It looks like it's not loading the driver, but I'm at a brick wall where trial and error isn't helping and I'm apparently not searching for the right info because I can't turn up anything on how to fix it.  :(

All I'm finding is stuff about getting Airport Extreme cards working and this isn't one.  It's the original Airport card which (iirc) is some sort of orinico card.

Here is some data:

iwconfig
```
aabrown@clair:~$ iwconfig
lo                 no wireless extensions.

eth0            no wireless extensions.
```

modprobe
```
aabrown@clair:~$ sudo modprobe airport
FATAL:  Module airport not found.
```

ifconfig
```
aabrown@clair:~$ ifconfig
lo                Link encap: Local Loopback
                   inet addr:127.0.0.1   Mask:255.0.0.0
                   UP LOOPBACK RUNNING MTU:16436  Metric:1
                   RX packets:0 errors:0 dropped:0 overruns:0 frame:0
                   TX packets:0 errors:0 dropped:0 overruns:0 frames:0
                   collisions:0 txqueuelen:0
                   RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
``` 

Help a noob out?  Unless my frustrations are clouding my brain, I was unable to find a solution on the forums or the Wiki.

aaron

---

### Post by Sensai28 on 2008-03-10
I have the same problem. I installed Ubuntu 6.06 a few days ago with a live CD then upgrade to 7.04 through software update. After a few software installs and a kernel upgrade, the airport card stop working.

I tried reformatting and reinstalling with the Live CD with no change. I even tried formating and installing Mac OS X. It still doesn't work. I'm new to GNU/Linux and I'm afraid I totally ruined my iBook.

Any help would be greatly appreciated.

---

### Post by Sensai28 on 2008-03-11
I think I found a fix. Under Terminal I typed:

sudo apt-get install linux-source

then

sudo apt-get install linux-headers-2.6.20-16-powerpc-smp 2.6.20-16.35

Next thing you know, I got wireless back. I hope this helps. Good luck.

---

