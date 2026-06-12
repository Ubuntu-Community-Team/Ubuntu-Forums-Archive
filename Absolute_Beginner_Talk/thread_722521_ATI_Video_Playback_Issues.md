---
title: "ATI Video Playback Issues"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by epitaph123 on 2008-03-12
**_To all ati users who are having video playback issues with the compiz CUBE enabled_**

I can now watch videos with the compiz CUBE enabled!!!

Steps to how I got it working.

1. sudo gedit etc/x11/xorg.conf

2. under the section device (shown below): I changed "opengloverlay" to off
                                                                                (originally it was on)

Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
	Option		"VideoOverlay"	"off"
	Option		"OpenGLOverlay"	"off"
EndSection

3. save & reboot.

you should now be able to watch videos with the cube enabled!

---

### Post by EnergySamus on 2008-03-12
My Friend's desktop was having this issue, I will tell him about this post.

EnergySamus

---

