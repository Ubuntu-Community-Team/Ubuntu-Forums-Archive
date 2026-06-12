---
title: "Video Card Installation"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by CtrlAltDelete on 2006-11-28
I just put a new video card (pny) into the pci slot....and a black screen. My old "video card" was built into the mother board

Please help!

---

### Post by taurus on 2006-11-28
Go into the BIOS and disable the onboard video card!  Then boot into the recovery mode from GRUB menu and at the prompt, reconfigure your X again with the new video card...

```
dpkg-reconfigure xserver-xorg
```

---

### Post by nickburns on 2006-11-28
try

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

this will back up your old xorg file, then do

sudo dpkg-reconfigure xserver-xorg

then you'll need to restart x (ctrl+alt+backspace)

wait 10 seconds for restart

---

### Post by CtrlAltDelete on 2006-11-29
I have a pny card- what is my x server driver?

sorry if this is a really noobish question

---

### Post by taurus on 2006-11-29
PNY is the name of the company like eVGA, XFX, Rosewell, etc.  It's probably nVidia.  What does it say on the box that it comes with or it should say on the video card itself?

---

### Post by CtrlAltDelete on 2006-11-29
is nevida nv?

---

### Post by taurus on 2006-11-29
If it's nVidia, then you have to use nv when you configure it and once you have X running, you can install nvidia driver for it.  So for now, choose nv for your video card.

---

### Post by CtrlAltDelete on 2006-11-29
After the reboot i cannot startx. Error:Microcode "bcm43xx_microcode5.fw" not available or load failure

---

### Post by taurus on 2006-11-29
Sounds like a wireless card's module but I could be wrong !!!  Do you have a wireless card on your machine or something?

---

### Post by CtrlAltDelete on 2006-11-29
yeah i can't get that to work either

should i take it out?

---

### Post by taurus on 2006-11-29
Yes, remove it because it is causing your machine not to boot.  Get X running first with your new card and then try the wireless after that.  Solve one problem at a time...  ;)

---

### Post by CtrlAltDelete on 2006-11-29
Well that was a good try, but it didn't work. Not the wireless card.

I try a start x and : XIO:fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 request (0 known processed) with 0 events remaining

---

### Post by CtrlAltDelete on 2006-11-29
It also reads Fatal Server error: no screens found

---

### Post by taurus on 2006-11-29
Did you reconfigure your X at all?

---

### Post by CtrlAltDelete on 2006-11-29
> **nickburns said:**
> try

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old

this will back up your old xorg file, then do

sudo dpkg-reconfigure xserver-xorg

then you'll need to restart x (ctrl+alt+backspace)

wait 10 seconds for restart

I followed this. After I performed teh Ctrl+alt+backspace. I have run into this problem

---

### Post by nickburns on 2006-11-29
Copy back your xorg.conf file to what we had originally.  Get to a terminal and type:

sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf

and this will at least get you back to where you were.

---

