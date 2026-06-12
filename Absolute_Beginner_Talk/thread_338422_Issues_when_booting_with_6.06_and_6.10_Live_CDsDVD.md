---
title: "Issues when booting with 6.06 and 6.10 Live CDs/DVDs"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by Gnelg on 2007-01-14
Hello all,

I will start by giving you some background and my system specs.

I am by no means an expert with Linux, but I do consider myself a fairly capable user.

I have been using Linux since kernel 1.3.6 in 1995. I have worked with countless different distributions in my quest to find the Linux that is right for me.  I am ready to get beyond this point and really understand how it works so that I can give back to the community.

My system specs:

MLB: Asus A8N SLI-Deluxe
CPU: AMD Athlon 64 FX-55 1MB cache 939
Video: EVGA Geforce FX-7800 GT 256mb
Memory DDR 4x512MB PC3200 Extra-low Latency 400Mhz Dimms from PQI
Drives:
Western Digital Sata2 250GB 
Memorex 16x DVD+-RW
Toshiba DVD-Rom


I have experienced a similar issue with several distributions recently but I'll stick to Ubuntu here.  When I boot a Live CD/DVD all seems to be working fine.  X starts and the start up music plays completely through then the splash sceen for Gnome comes up garbled with horizontal lines and my system locks.  I have to power off and cold boot and come back to the same thing.  I have been able to use the Boot in Safe Mode option using 6.06 but 6.10 still has the same problem.  

Along these same lines in 6.06 the initial splash screen with the Ubuntu graphic looks fine but with 6.10 it is black and white(greyscale)

I have been able to complete an install with 6.06 and then install the driver from Nvidia and the issue goes away, but I'd like to find a way to not have to workaround this issue just to get things up and running.

Any help is appreciated.  

Please feel free to ask any questions if I have not provided enough info.

Gnelg

---

### Post by xpod on 2007-01-14
You could always try an alternate cd.....no live session to try but installing can be a bit less problematic.:D 
Having to install your nvidia driver once you got dapper(6.06) up & running aint really a workaround so much as a requirement.Especially if you want the advanced graphics & 3d etc.

Cant really tell you much more as i`ve only been using Linux since last july.
Hell,i only switched a pc on for the first time not long before that.

All i know is my sanity has returned since getting Ubuntu(sort of);) 

Good luck

---

### Post by rai4shu2 on 2007-01-14
What type of monitor?

The B/W usplash is a known issue in Edgy amd64.

[https://launchpad.net/ubuntu/+source/usplash/+bug/67545](https://launchpad.net/ubuntu/+source/usplash/+bug/67545)

---

### Post by livinginx on 2007-01-14
On my 2nd box, I get weird issues with the video card. 

I have an ASUS NVidia 6200 card running on an MSI motherboard.  After doing some research, I learned that there is something in the mobo chipset that it actually prefers radeon cards.

I know, sounds really stupid and I am not sure if that is a big part of it.

But the other thing I learned is that certain newer cards are not 100% supported under Linux.  You should be able to boot in VGA mode and configure it from there.

---

### Post by Gnelg on 2007-01-14
Monitor is a ViewSonic 19" VX924 LCD

---

