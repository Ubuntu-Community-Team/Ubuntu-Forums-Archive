---
title: "Dell Inspiron 2200 Screen Resolution"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-04-22
The only screen resolution I can get is 1024x768. I want to make things smaller. I don't know what kind of graphics card I have. If someone can tell me what I need to type in the terminal so I can figure out what card I have it would be a start.

---

### Post by Kobalt on 2007-04-22
Try this : open a Terminal and type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
From there select the resolutions you want as available by hitting the spacebar, then validate and restart X by pressing Ctrl+Alt+Backspace.

---

### Post by tdrusk on 2007-04-22
> **Kobalt said:**
> Try this : open a Terminal and type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
From there select the resolutions you want as available by hitting the spacebar, then validate and restart X by pressing Ctrl+Alt+Backspace.
All that did was make my screen go black, then return to my original resolution.

---

### Post by tdrusk on 2007-04-22
anybody?

---

### Post by Disa on 2007-04-22
Same thing here, on my Inspiron 8000.  The only resolution settings it offers me are 640x480 and 800x600, when my native resolution is 1600x1200.  I tried the command that was suggested here, and all that happened is the screen went black for a second, and then the display came back as if nothing had happened.

EDIT (added): Oh yes, and I checked my /etc/X11/xorg.conf file, and it shows the only resolution at all color depths to be 1600x1200, but that apparently has no bearing on what resolution choices it offers me.  Strange too, since on my desktop computer (with an nvidia card), I was able to get the resolution I wanted just by adding it in there.

---

### Post by st33med on 2007-04-22
Tell us what your lspci output is. Then we'll help.

---

### Post by tdrusk on 2007-04-22
> **st33med said:**
> Tell us what your lspci output is. Then we'll help.
That was the command I was looking for. :)
```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

---

### Post by st33med on 2007-04-25
Ahhh! You need 915 resolution! Go to this webpage and follow their instructions.
[http://ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

PS: Srry for the long response!

---

### Post by H.E. Pennypacker on 2007-05-06
Same laptop here!

You might be interested in another thread as well:

[http://ubuntuforums.org/showthread.php?t=358432&highlight=blank+screen](http://ubuntuforums.org/showthread.php?t=358432&highlight=blank+screen)

It is regarding an entirely different problem.  Let me know if you have any other problems.  I have had my Inspiron 2200 for quite a while, and I may be able to help you with a few things.

---

### Post by ramjet_1953 on 2007-05-06
Sorry to disagree with you, st33med, but if he is using Feisty 7.04, 915resolution is "Old Hat"

Copy and paste this command into a terminal [COLOR="Red"]sudo apt-get install xserver-xorg-video-intel[/COLOR]

This will download and install the latest and greatest Intel video driver.

It is fully automatic and after re-booting, it should come up in the optimal video mode for your system.

If you have already installed 915resolution, I would un-install this package first.

Regards,
Roger 8)

---

