---
title: "Radeon 9800 problems (was:PowerPC Installation, PowerMac G4 (Quicksilver))"
date: 2015-08-04
forum: Apple Hardware Users
---

### Post by AnttiV on 2015-08-04
Hi!

I have had old PowerMac G4 lying around and I figured I'd try to get it running something more current than the Mac OS X 10.5 which was installed on it. First I wanted to try MorphOS and even installed it and everything was running fine - then I found out about MorphOS licensing and the prices and went nope.png.

I figured - since my other machine is a Xubuntu one - to give Lubuntu PPC a go (because free and I like DEB-based distros anyway).

So I downloaded the Lubuntu 14.04.2 LTS iso (powerpc variant, not the ppc64el), threw it at dd and made a USB stick with it. Holding down alt to get to bootmenu on the G4 and I was able to boot into the Live installation.
Everything seemed to work well enough, so I started installation. But then after awhile it gets stuck, "nothing" happens. Yes, I can move the mouse, but I'm unable to click buttons, icons or move the installer window. I tried three times and with various differences, the result was always the same: it gets stuck/ hangs about 2/3rds of the way in. Specifically:

First try: Hangs on the "select time zone" screen. The "continue" button never turns active and just stays grayed out.
Second: Hangs before that screen, right after partitions are made on the disc. (I chose the "Erase entire disk and install" each time).
Third try: like second one.

Any pointers on what should I try?

 I don't have any other PPC machines around, but have plenty of x86/x64 systems running various operating systems.  The MorphOS 3.9 run perfectly well, so I don't think there's anything physically wrong with the machine (it also booted well into the OS X right before I installed MorphOS). It's a Dual 1GHz G4 with 1.25Gb or RAM and a single 80Gb HDD. The graphics is handled by a Radeon 9800 Pro (VGA connector). There's nothing else besides keyboard, mouse, the usb stick and network connected to the machine (and obviously power and display). 

After I type this down, I'm going to try and fine another HDD to test (since it always hangs close enough after partitioning), though I don't believe there's a probleb with it, since MorphOS and Mac OS X worked well, but I'll try anyway. 

Is there a way to run the installer in a "verbose mode" so I could see what it is doing, or does anyone have any bright ideas? :D

EDIT: Alternate CD image let me install it in text mode just fine. Now can't boot into it without "video=ofonly" and it still freezes

---

### Post by howefield on 2015-08-04
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by AnttiV on 2015-08-05
Update: Tried Ubuntu MATE (powerpc) and it hangs at the exact same spot, right when timezone is selected. Sometimes I can press the button and it hangs, sometimes the button stays greyed out and I can't even click on it and then it hangs.

Tried two different HDDs, everyone has the same problem while MorphOS installs to each HDD perfectly and has no problems. It's Lubuntu/Ubuntu MATE that has this problem thus far.

---

### Post by rican-linux on 2015-08-05
Which ISO are you trying?

---

### Post by AnttiV on 2015-08-05
lubuntu-14.04.2-desktop-powerpc.iso and ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso, with links from [https://wiki.ubuntu.com/PowerPCDownloads](https://wiki.ubuntu.com/PowerPCDownloads)

EDIT: And md5sum checks out with those posted on each page, so the downloads are ok.

---

### Post by rican-linux on 2015-08-05
what is your video card?

---

### Post by AnttiV on 2015-08-05
Like I said in the first post, a Radeon 9800 Pro ;)

EDIT: It's not the installer. I booted to both of the system and let it just be and just moved the mouse and opened/closed some windows. It crashes without even trying to install. After approx. 2 minutes after it has booted, it freezes/hangs/whatever you want to call it. I figured it might overheat (Because dual G4. They're infamous of getting hotter than hell.) So I opened the case and put a good 120mm fan right on top of the CPU cooler. Didn't have any effect, still crashes after ~2mins uptime.

I highly doubt it would be because of hardware, since MorphOS and Mac OS X itself were/are perfectly stable. Something in the *buntu live CD makes it freeze after 2 minutes.

---

### Post by dand1972 on 2015-08-06
Since you're using the graphical desktop installer, you should have better luck with the alternate cd (text-based). Go here:

[http://cdimage.ubuntu.com/lubuntu/releases/14.04.2/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04.2/release/)

and choose the alternate powerpc image.

---

### Post by AnttiV on 2015-08-07
Okay, that helped... a bit. I got the system installed, but that's pretty much the extent of how much it works right now. 
If I just let it boot, it gets to the screen with "Lubuntu" and four dots under it (note that this is a text-screen, not graphics like it "should" be). Right after that it loads a "graphical" screen but it stays black with a mouse pointer. Nothing happens after that. I can change to tty1 and login in text mode (I did this and run apt-get update / upgrade, and while it did upgrade a bunch, it did not help).

If I boot with "Linux video=ofonly", I get the graphical "Lubuntu with four dots under it" screen and then a normal-looking login screen. I can log on and then pretty much it freezes. I managed to open "System profiler and benchmark", but the window was blank and it freezes right at that point.

So yeah, it pretty much is my videocard that I have problems with, or at least I can't figure out another culprit at this point.

EDIT: booting with "radeon.agpmode=-1 video=ofonly" seems to have helped at least for the first minutes - it's been on for 2-3 minutes without freezing. I'll follow the situation :)

EDIT2: Yeah, that seems to have done it. It has worked now almost two hours without crashing. The 2D performance is a tad slower than I though, but at least it isn't crashing :)

---

### Post by rican-linux on 2015-08-08
also try this 

```
 radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

---

### Post by AnttiV on 2015-08-08
> **rican-linux said:**
> also try this 

```
 radeon.modeset=1 video=offb:off video=radeonfb:off radeon.agpmode=-1
```

I saw that in another thread after I tried the last one. What does that do, exactly, and should I use that instead of the one I'm using? As in, is one of the lines somehow "better" than the other? Since mine *is* actually working now with "radeon.agpmode=-1 video=ofonly", do I gain something from changing the boot parameters?

That said, I will probably try that anyways and see what happens, but I'd like a (short) explanation of the why and what of it :)

---

### Post by este.el.paz on 2015-08-08
AntiV:

Short answer: the radeon driver is not supported in 14.04.  But, main thing is, if it's working it's working.  In my iBook with the radeon card I use "video=ofonly radeon.agpmode=-1"  and that's all I need.

e..

---

