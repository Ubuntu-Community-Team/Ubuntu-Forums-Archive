---
title: "Problems when running 1280x1024 resolution"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by dononvanb on 2007-08-25
Hi,

when i run ubuntu on the 1280x1024 resolution, there are a couple of strange vertical lines on my screen. I thought it had something to do with vertical and horizontal frequencies, so I looked into the book of my screen and edited xorg.conf. But still there are those lines (however they look not the same as before). If I choose 1024x768 everything is fine. On Windows with resolution 1280x1024 everything is fine too.
Does somebody know which is the source of this problem? In the book of my screen I saw that "Pixel Clock (mhz)" is mentioned, I don't know if this has anything to do with my problem.

Thanks

---

### Post by wjp.reg on 2007-08-26
what brand/model of video card is running on your computer?

Can you post the output of the following command:

```
 lspci | grep "Display"
```

---

### Post by dononvanb on 2007-08-28
Thanks for your reply
lspci | grep "Display" returns nothing, lspci returns the following:

> 00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 11)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 11)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 11)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 11)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 11)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 11)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)
01:0c.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)

My video card is an Intel 82815.

Thanks

---

### Post by alienexplorers on 2007-08-28
Do you have the correct drivers running for your video card.  have you tried the 915resolution drivers.

---

### Post by wjp.reg on 2007-08-28
I found [this]("https://lists.ubuntu.com/archives/ubuntu-bugs/2006-February/138730.html") reference to the same problem you described.

Perhaps you can also double-check the refresh rates for your graphics controller.  Here's another link pertaining to your [graphics driver and changing resolutions]("http://www.linuxforums.org/forum/debian-linux-help/67430-how-increase-resolution-2.html").

Hope this helps.

---

### Post by dononvanb on 2007-08-29
My problem is solved.  \\:D/
I followed a link given by wjp.reg and that told the solution.
Changing the color depth from 24 to 16 solved the problem. 
(I don't see any difference between 24 and 16, is that normal?)

So thanks a lot ubuntu community and especially wjp.reg =D>

---

### Post by wjp.reg on 2007-08-29
Ah shucks.

It's so nice to be appreciated, :popcorn:

Glad things worked out for you.

---

