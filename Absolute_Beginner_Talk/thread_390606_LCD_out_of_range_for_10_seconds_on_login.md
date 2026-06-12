---
title: "LCD out of range for 10 seconds on login"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by gliderman on 2007-03-22
My LG Flatron L1750SQ displays "OUT OF RANGE 36.8 khz / 82 Hz" for about 10 seconds before I see the kde loading screen.

It has done this since I installed Dapper even though i have ran: 
"sudo dpkg-reconfigure xserver-org" and set my monitor's horizontal and vertical scan frequency from an information booklet on the web. (horizontal scan frequency 30-83kHz, vertical scan frequency 56-75 Hz).

---

### Post by justleen on 2007-03-22
out of intrerest, what version did you install?
I had exactly the same on my LG177S when installing Xubuntu: any thing not in X gave an out of range on my monitor. (even once logged on in GDM, and pressing alt-ctrl-F1 for a terminal gave an out of range)
Solution for me was to not the use the VGA output on my video card, but use a dvi donlge and the dvi output..

The "normal"  ubuntu worked fine on the same system though.. not sure what was going on there..

---

### Post by wpshooter on 2007-03-22
> **gliderman said:**
> My LG Flatron L1750SQ displays "OUT OF RANGE 36.8 khz / 82 Hz" for about 10 seconds before I see the kde loading screen.

It has done this since I installed Dapper even though i have ran: 
"sudo dpkg-reconfigure xserver-org" and set my monitor's horizontal and vertical scan frequency from an information booklet on the web. (horizontal scan frequency 30-83kHz, vertical scan frequency 56-75 Hz).

What video card are you using ?

---

### Post by gliderman on 2007-03-22
I've solved the problem by changing the bootup resolution. 

I added vga=795 to 
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
in menu.lst (/boot/grub)

Now its boots in 1280x1024 resolution but the refresh rate is 60Hz instead of 75Hz which is what it is in kde? How do i make the refresh rate 75Hz at bootup?

Source: HOWTO: Change bootup and console resolution
[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

Im using an ATi Radeon 9600 Pro 256Mb video card

---

