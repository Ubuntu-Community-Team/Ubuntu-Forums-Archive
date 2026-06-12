---
title: "Wireless DWL-122 Ubuntu 7.04"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by giantsavage on 2007-08-29
Hi Everyone,

I am brand new to the Linux world, and decided Ubuntu 7.04 looked like it would be a good start for me.  I have finally installed Ubuntu on my Windows Vista Machine.  It now works in dual boot mode.  I guess the very next step to continue learning linux is to get my wireless internet connection up and running.  I have downloaded the linux-wlan-ng-0.2.8 I have placed it on my usb drive which works in linux.  I have even extracted the package into the same directory on my USB drive.  Next I need to know where to place it on the regular hard drive (ie. /home/savagepa/src)  that is a directory I have made in my home directory.  To be honest I have been unable to even get to the install of the package onto Ubuntu as of yet.  I have read all the posts about how to do this and it still isn't flowing in my mind as I read it.
I have come to the conclusion that I need to build the kernel before I can install wireless drivers.  so I downloaded linux-source-2.6.20 and extracted to the directory I mentioned above.  Is this the right source for the Kernel for Fiesty?
I tried following the instructions in the read me file that came with the source and when I got to the stage of running the comands included to build the kernel all I got was errors.  Modules not enabled or something along those lines.

Please help me start this right from the begining, assuming I have the right Kernel Source please walk me through the very next steps.  I am eager to learn linux but I think an internet connection is a must to read these forums and be on linux at the same time.

I will follow your instructions to a tee and will provide back exact problems I run into.   Please keep in mind that I am brand new at Linux when providing the instructions.

Thank you for your patience and your help.

Pat

---

### Post by julian67 on 2007-08-29
I have one of these as well (it came bundled with wireless router) but couldn't get it working...your post prompted me to search some more and I found this howto [http://www.shaftek.org/blog/2005/02/10/dlink-dwl-122-usb-on-fedora-core-2/]("http://www.shaftek.org/blog/2005/02/10/dlink-dwl-122-usb-on-fedora-core-2/") which is for fedora but according to a post [here]("http://www.bleepingcomputer.com/forums/topic99801.html") works fine with Feisty. I'm away from home now and don't have the d-link adapter with me but I'll be trying it next week. Maybe you can try it and post? 

btw I found a nice Safecom USB wi fi dongle based on zydas 1211 chipset and it works perfectly. just plugged it in, network manager saw it and supports WEP & WPA perfectly....also it really has much better signal strength & hangs onto the signal much better than the Intel ipw2200 built in to the laptop.

---

