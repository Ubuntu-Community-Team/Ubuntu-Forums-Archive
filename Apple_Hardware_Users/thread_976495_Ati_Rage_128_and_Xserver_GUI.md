---
title: "Ati Rage 128 and Xserver GUI"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by JacaByte on 2008-11-09
I've gotten a distribution of Linux to boot into the GUI interface on any computer for the first time in about 3 years when I was experimenting with Knoppix! The only problem is, well, the GUI doesn't work completely.

On boot up I get the an error message telling me that screens were found, but "none have a usable configuration." No biggie, I can still get to login screen (which appears to be running in 640x480 at 256 colors) and log into the desktop , but when I try to open windows they'll pop up onto the screen and then disappear as fast as they came. It's really frustrating; the only way I can use the machine for now is via the failsafe command prompt.

Now, when I was sifting through solutions for getting Debian to work on the powermac about 2 years ago, I found out that it has an Ati Rage 128 video card, which requires a special set of drivers in order to be utilized. I found the driver for my card [here]("http://packages.ubuntu.com/intrepid/xserver-xorg-video-r128") but I want to know if it will 1) work on Xubuntu 8.10 2) is it likely to solve my problem at all (since I tried the package for Debian 2 years ago and it was a no go) and 3) how would I go about installing it in the first place? (I assume it's just "sudo aptget xserver-xorg-video-r128"?)

---

### Post by stream303 on 2008-11-09
You shouldn't have to download any specific drivers, although sometimes the hardware isn't detected properly and you have to manually specify it - usually in /etc/X11/xorg.conf.

The detection problem is usually the fault of the fact that Apple hardware isn't designed to be easily / properly probed by anything other than OSX, but the Linux devs do their best without any adequate support documentation.

Sounds like you have an Intel-based Xserve - maybe someone can give you some pointers with the r128...

---

### Post by JacaByte on 2008-11-09
Eh, no. It's a PowerMac 9500 upgraded to a G3, so it's an oldworld PowerPC. It can't run OS X, just Xubuntu and OS 9 for the moment. I kinda of left that out, sorry...

I'm positive the grahpics card is a 128 Rage.

---

### Post by cyberdork33 on 2008-11-09
> **JacaByte said:**
> Eh, no. It's a PowerMac 9500 upgraded to a G3, so it's an oldworld PowerPC.
Your thread title is misleading. I thought you were talking about an Xserve too.

---

### Post by JacaByte on 2008-11-09
I'm sorry about that, I must have meant the Xfce system. I wish I were dealing with an Xserver, but that's not the case. I'll change the title...

Edit: Ah darn, I can't change it with this forum software.

---

