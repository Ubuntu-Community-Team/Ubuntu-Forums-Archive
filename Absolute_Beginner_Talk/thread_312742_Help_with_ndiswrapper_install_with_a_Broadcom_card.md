---
title: "Help with ndiswrapper install with a Broadcom card (Microsoft MN-730)"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by crazybrit4967 on 2006-12-04
Hi everybody!

I've been using Ubuntu for a few months now, and one of the things  that has kept me from using it as my primary OS is not being able to connect to the internet properly.  See, I have a Microsoft MN-730 wireless card (it's a Broadcom chipset, apparently), which isn't supported by Ubuntu.  I tried using bwm43xx-fwcutter for a while, but the connection was too slow and sometimes didn't work.  So I decided to try using ndiswrapper - here's what I did so far:

[LIST]
[*]Installed Ubuntu Edgy
[*]Installed ndiswrapper-utils-1.8
[*]sudo ndiswrapper -i (driver path)/mn-720.inf (note - I used this instead of the standard bcmwl5.inf at the suggestion of a commenter in one thread - it's the driver from the CD that came with the card).
[*]sudo ndiswrapper -m
[*]sudo modprobe ndiswrapper
[*]sudo gedit /etc/modprobe.d/blacklist - added "blacklist bcm43xx" to the end
[*]sudo gedit /etc/modeprobe.d/ndiswrapper - changed eth1 (the name of the wireless interface when I was using fwcutter) wlan0
[*]gksudo gedit /etc/modules - added "ndiswrapper" to the bottom
[/LIST]

Then I set everything up correctly in System>Administration>Networking and, surprisingly, the web still doesn't work.  Anyone know what's going on?  Please?

---

### Post by kelbizzle on 2006-12-04
I installed my broadcom 43xx card using the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=197102").
With those drivers below. Your drivers might be different though.

---

### Post by crazybrit4967 on 2006-12-04
> **kelbizzle said:**
> I installed my broadcom 43xx card using the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=197102").
With those drivers below. Your drivers might be different though.That script should just automate what I already did.   Do you know of anything that the script will do that I haven't tried?

---

### Post by crazybrit4967 on 2006-12-04
So... can anyone help?  Pleeeease?

---

