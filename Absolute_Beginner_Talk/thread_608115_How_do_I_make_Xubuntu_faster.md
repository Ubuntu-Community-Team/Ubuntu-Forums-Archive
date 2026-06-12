---
title: "How do I make Xubuntu faster?"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Vongzilla on 2007-11-09
Hi all,

I got a geek itch lately and decided to try Linux (again) after a 5 year hiatus.  I resurrected an old Thinkpad 570 w/192mb RAM, 6gb hd and a NeoMagic 2.5mb video card.

I wanted to build an OS image that was useful and snappy on such a dated machine so I installed Xubuntu with the XFCE windows manager.  Everything works fine, but I am surprised to see that it is much slower than WinXP.  Sure, Xubuntu probably uses a lot less ram than WinXP, but the responsiveness of the UI is lacking.  Scrolling through documents or web pages doesn't result in a clear redraw until I stop scrolling.  I'm thinking this is mostly due to the graphics driver/Xserver I think.  X says it has the right driver for the NeoMagic card, but the UI doesn't have the snap that WinXP does.  This wasn't an issue when I tried out Ubuntu via a VirtualBox install.  Then again, that was on a modern machine.

So how do I get X to go faster?  Are there better drivers for the Neomagic chipset available?  Are there any tweaks to Xconfig file I can make?  This may seem like a small gripe, but it really takes the fun out of using Xubuntu for creating documents and surfing the web.

Thanks,
Thomas

---

### Post by kerry_s on 2007-11-09
are you using the neomagic driver?

```
[B]sudo mousepad /etc/X11/xorg.conf

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"neomagic"
#	Driver		"vesa"
	Option		"StrangeLockups" "false"
        Option             "OverlayMem" "829440"
EndSection
[/B]
```

also mine has to use 16 for color->

```
[B]Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768" 
	EndSubSection
EndSection[/B]
```

don't forget to restartx after the changes, logout and press ctrl+alt+backspace

---

### Post by TeaSwigger on 2007-11-09
Not sure Xubuntu's light enough to be exactly "snappy" and fast on that thinkpad. At least without a lot of customizing, server install on up, I'd guess. Considered Fluxbuntu?
[http://www.fluxbuntu.org](http://www.fluxbuntu.org)
Or perhaps a light distro, Puppy Linux or something?

---

### Post by markharding557 on 2007-11-09
A very light distro is damm small linux

---

### Post by Vongzilla on 2007-11-09
kerry_s hit it on the mark.  24-bit is unaccelerated.  I modified the config file to 16-bit and things are a lot faster.  I also googled this after my post and others have the same issue.  Most linux distributions default to the 24-bit unaccelerated screen modes.

I've seen Puppy Linux on the web and have read a little about it.  I think I'll try that next along with DSL.  I'm looking for a good balance of modern newb-friendly interface/software installation process/library and attractive UI with speed of the interface.

So the topic now kind of dovetails into what's the lightest/fastest usable distro with the above criteria?  What's the fastest newb-friendly windows manager?

Thanks again for your replies.

---

### Post by wolfvorkian1 on 2007-11-09
> **Vongzilla said:**
> kerry_s hit it on the mark.  24-bit is unaccelerated.  I 
So the topic now kind of dovetails into what's the lightest/fastest usable distro with the above criteria?  What's the fastest newb-friendly windows manager?

Thanks again for your replies.

I'm not sure changing the windows manager will help out that much. I've got openbox installed and granted it does go from the login almost instantaneously when Xfce doesn't but I haven't noticed the the various applications opening any faster in openbox than Xfce and the time from the login to being able to use a program really isn't significant compared to how long it takes the machine to boot up. So I seldom use openbox because of that and settle for Xfce which already has panels, etc. 

Puppy Linux is fun to play with though. It is lightning fast from the CD. I think I read where it loses much of it's speed though if you install it to the hard drive. I thought I had a brand new super machine the first time I clicked the web browser in Puppy the way it jumped to attention and went to work.

---

### Post by genbuntu on 2007-11-09
I also had a similar thread a while ago, asking for a fast ubuntu type distribution:

[http://ubuntuforums.org/showthread.php?t=605079](http://ubuntuforums.org/showthread.php?t=605079)
:)

EDIT: Aysiu recommended to use IceWM as a window manager. Haven't tried that yet, but I did try Puppy linux from cd. I found it quite fast enough.

---

