---
title: "Powermac G5/nvidia card can't get native resolution on cinema display"
date: 2006-06-06
forum: Apple PPC Users
---

### Post by megagram on 2006-06-06
I have a Powermac G5 with an Apple 20" cinema display attached to the Nvidia GeForce 5200 card and I can only get a max 1024*768 resolution after installing Ubuntu Dapper. 

I'm assuming I need to install the Nvidia drivers to get the native resolution of my display which is 1680*1050. However, I can't get the drivers.

I've tried adding the restricted repositories to the package manager but still nothing appropriate shows up when I search for Nvidia.

Can someone please help me?

Thanks in advance,

Graham

---

### Post by plush on 2006-10-27
Same here!  By the way, there are NO nVidia linux PPC drivers, just the default ones included with Ubuntu :(

---

### Post by stmiller on 2006-10-27
The cinema display is reported to work with ATI drivers. 

[http://forums.gentoo.org/viewtopic-t-392904-highlight-cinema+display.html](http://forums.gentoo.org/viewtopic-t-392904-highlight-cinema+display.html)

Might find a used AGP ATI Radeon card.

Unfortunately drivers for nvidia cards in PPC Linux suck; and ATI's aren't much better, but a little better. It is difficult to get good 3D support in PPC Linux, depending on your card.

---

### Post by stream303 on 2006-10-27
I just installed Edgy and had to change the generic default to NV at 1680x1050.  It may not be the fastest NV driver, but at least it will get you the proper resolution.  (fast enough for me...)  On disk so it was a breeze to install.

[http://ubuntuforums.org/showthread.php?t=284508](http://ubuntuforums.org/showthread.php?t=284508)

This worked with my 20" iMac now running Edgy (quietly too!)

---

### Post by plush on 2006-10-27
Hey stream303;  could you just very quickly explain how you went about setting the default resolution to 1680x1050??  Thx.

---

### Post by stream303 on 2006-10-27
Sure - in terminal:
sudo dpkg-reconfigure -fgnome -phigh xserver-xorg

Then just choose your driver in the dialog box that comes up (mine was NV) and your monitors native resolution.  A whole lot easier than manually editing xorg.conf!

Credit goes to this thread:
[http://www.ubuntuforums.org/showthread.php?t=280190](http://www.ubuntuforums.org/showthread.php?t=280190)

Remember that this worked on my G5 RevA 20" iMac ...

---

### Post by plush on 2006-10-28
Thanks.  I actually tried something else before you responded.  For the record, the xorg.conf settings below not only enable 1920x1200 native resolution for the Apple Cinema 23" aluminum display, it enables all the other resolutions (ie. 1680x1050, etc).  I've tried other modelines and some worked, some worked partially, this is definitively the best settings for my monitor:

> Section "Monitor"
Identifier "Cinema HD Di"
Option "DPMS"
HorizSync 28-96
VertRefresh 43-60
Modeline "1920x1200" 155.0 1920 1984 2016 2144 1200 1203 1206 1212 -HSync +Vsync
EndSection

Section "Screen"
Identifier "Default Screen"
Device	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
Monitor "Cinema HD Di"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1920x1200" "1680x1050" "1280x960" "1024x768" "800x600" "640x480"
EndSubSection
EndSection



Note:  Replace device with whatever your video card is.

[http://ubuntuforums.org/showthread.php?t=85109&highlight=apple+cinema+display](http://ubuntuforums.org/showthread.php?t=85109&highlight=apple+cinema+display)

---

