---
title: "Install/Resolution Problem Gateway M305CRV"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by vegipowrd on 2007-08-04
I'm having some problems installing Ubuntu on a Gatway M305CRV laptop.  The screen resolution is too low for me to see the entire install window.  I can't actually get to the stupid buttons at the bottom to advance the install process.  There seems to be no way to resize it (obviously, other windows will resize, but not install window) and I can't get the screen resolution settings above 800x600.  

I've done a few alternate CD Xubuntu installs this week, but I'm hesitant to do that now without knowing I'll be able to get 1024x768 after it's all done.  Previous posts on the resolution issue (for this exact GTW laptop) are quite old and not too encouraging. 

In particular, I'd like to see things work in 1024x768.  Can I do that from the Live CD, or must I install and hope I can figure it out later.

Ideas?

---

### Post by miltonics on 2007-08-07
I've just acquired a Gateway m305crv myself. 

First of all you can adjust the properties on the panels to show the hide buttons.  When the panels are hidden you have just enough screen real estate to navigate through most windows.  Also Alt+F7 and the arrow keys will allow you to move the windows to a semi-usable position if they are still too big.

I have been able to get 1024x768 resolution by using 915resolution and xserver-xorg-video-intel both of which are easily found by searching in Snaptic for 915.  I'm not really sure which is doing what, as my methods are none to sophisiticated.

The troubles I'm having are related to playback of video, and the wireless, both of which are not working right now and the fact that it will never shut down, it just reboots instead.

I'm planning on messing around with the video drivers, trying out the newest version of ndiswrapper (1.47) if I can get it installed, and possibly upgrading the bios, to fix each of those problems respectively.

---

### Post by vegipowrd on 2007-08-07
I actually tried getting rid of the pannels, but it didn't solve my problem.  

It looks like 915resolution may be the best bet fot this machine, though I haven't gone that route yet.  

Amazingly I had no problems with wireless.  My PCIMCIA slot hasn't worked for years, so I got a USB wireless adapter.  I was flored when I could surf the web instantly after booting from the liveCD (BestBuy had a sweet sale on Belkin F5D8053).

---

