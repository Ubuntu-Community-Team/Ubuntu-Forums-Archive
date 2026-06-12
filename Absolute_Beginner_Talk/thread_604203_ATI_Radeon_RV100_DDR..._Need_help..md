---
title: "ATI Radeon RV100 DDR... Need help."
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by johnmata on 2007-11-05
I am running Gutsy and am having a hell of a time getting dual monitors to work.  I am using an ATI Radeon RV100 DDR, AGP card with dual VGA's.  I think the problem is with the driver because not matter what I do Ubuntu loads a generic driver which yields very low resolution and mirrored screens.  I could really use some help.  I appreciate any advice.

Regards,
John

---

### Post by manishk on 2007-11-06
> **johnmata said:**
> ...not matter what I do Ubuntu loads a generic driver which yields very low resolution and mirrored screens...
John

Does your card show up in the 'Restricted Driver Manager'??

---

### Post by twiceasworn on 2007-11-06
I don't have a solution.  This happened to me when I upgraded to gutsy and I could not for the life of me get it fixed.  The farthest i got was mirrored screens in the correct resolution.  I ended up just going back to feisty, where dual monitors worked.  Good luck.

---

### Post by moon2js on 2007-11-06
> **manishk said:**
> Does your card show up in the 'Restricted Driver Manager'??

If my card doesn't show up there, what does that mean? I have two old computers, one with a ATI Radeon 7000 and the other with a 7500 (both AGP). Is there a difference between an "ati" driver and a "radeon" driver?

---

### Post by ddoxey on 2007-11-06
After the Gutsy update, my dual head ATI Radeon setup doesn't work any more.

I suspect these lines in my Xorg.0.log are of interest:
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "MergedFB" is not used
(WW) RADEON(0): Option "MonitorLayout" is not used
(WW) RADEON(0): Option "MetaModes" is not used
(--) RandR disabled
...

It appears that I'm now in the realm of XRandR configuration.

After Xfce starts, and I'm looking at my mirrored screens, I can fix it by executing;
$ /usr/bin/xrandr --output VGA-0 --mode 1280x1024 --right-of DVI-0

To make this automatic, I added it in the "Autostarted Applications" GUI tool.
The result is a mirrored screen configuration until Xfce is finished initializing, then things wink out briefly and return in dual screen mode.

I think this solution would work equally well with mirrored screens on nVidia.
However, someone else will have to test that.

---

### Post by ddoxey on 2007-11-06
Yes, there is a difference between the "ati" and "radeon" drivers.

Here's the doc on the "ati" driver:
[http://ftp.x.org/pub/X11R7.0/doc/html/ati.html](http://ftp.x.org/pub/X11R7.0/doc/html/ati.html)
And a little on the history of the driver:
[http://ftp.x.org/pub/X11R7.0/doc/html/ati10.html#32](http://ftp.x.org/pub/X11R7.0/doc/html/ati10.html#32)

Here's the doc on the "radeon" driver:
[http://ftp.x.org/pub/X11R7.0/doc/html/radeon.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/radeon.4.html)

It appears they were written to support different hardware, and they were written by different developers.

In researching my on problems on x.org, I discovered there is a similar relationship between the "nv" and "nvidia" drivers.

---

### Post by moon2js on 2007-11-07
According to [a Ubuntu ATI Radeon open-source driver HowTo]("https://help.ubuntu.com/community/RadeonDriver"), my (old) card should be well supported by the open source radeon driver, and I get the feeling it should be set up correctly automatically in Gutsy. I don't have to do anything to change it from "ati" to "radeon", do I?

I'm having a lot of trouble getting a dual head config. I added a Virtual line in my xorg.conf for  2560x1024, so I could have two 1280x1024s side-by-side. Mirroring works fine, but when I try to extend the desktop with something like:

```
$ xrandr --output VGA-0 --right-of DVI-0

$ xrandr --output DVI-0 --right-of VGA-0

$ xrandr --output VGA-0 --left-of DVI-0

$ xrandr --output DVI-0 --left-of VGA-0
```

...I get one garbled monitor (a very fine, static completely garbled screen) and the other monitor appears somewhat weird and divided, with half of it behaving normally and the other half shows windows/desktop (but doesn't change/respond to anything). My terminal window appears in the middle of that nongarbled screen and I have to drag it to the working half so I can restore my monitors back to mirror, and the part of the terminal window on the dead side just stays there frozen. Yet the mouse cursor moves across both monitors correctly as if they were one desktop.

my xrandr output is:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right) 376mm x 301mm
   1280x1024      60.0*+   75.0     59.9  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected 1280x1024+0+0 (normal left inverted right) 300mm x 225mm
   1024x768       75.0 +   84.9     75.1  
   1280x1024      59.9* 
   800x600        84.9     75.0  
   640x480        84.6     75.0     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right)
```

I figure I've got some concept wrong or my geometry is off. Anyone have any ideas?

---

### Post by moon2js on 2007-11-07
> **johnmata said:**
> I am running Gutsy and am having a hell of a time getting dual monitors to work.  I am using an ATI Radeon RV100 DDR, AGP card with dual VGA's.  I think the problem is with the driver because not matter what I do Ubuntu loads a generic driver which yields very low resolution and mirrored screens.  I could really use some help.  I appreciate any advice.

Regards,
John

Did you do anything after updating to Gutsy?

The same thing happened to me (start up in ugly-mode/VESA/generic driver mode) with the same video card after I edited xorg.conf per a howto for dual-head screens. I found out that my syntax was slightly off (Virtual) and after fixing that, graphics worked normally (resolution, etc), but still I can't get dual-head (as you can see from my above post).

---

