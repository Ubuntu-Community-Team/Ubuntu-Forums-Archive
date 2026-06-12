---
title: "Problem on Ubuntu Display"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by toshi.readman on 2007-09-25
When I first got the Ubuntu 6.06 LTS and tried installing it (along with my Windows XP), the display is fine, the movies are great, my images are crisp and everything in the monitor is well. But when I reformatted my hard drive (and wiping off XP) and installed feisty fawn, everything went wrong. I cannot watch my movies right now, the images are 'discolored' and the menus, icons etc. have lots of blueish vertical lines on them. I am posting here a the screenshots of what I am talking about.

[http://picasaweb.google.co.uk/jancarlocruz](http://picasaweb.google.co.uk/jancarlocruz)

I tried replacing my video card and my monitor but everything stayed the same. Please help!

---

### Post by CaptainInsaneO on 2007-09-25
Have you tried reinstalling your video drivers?

---

### Post by alienexplorers on 2007-09-26
What type of video card are you using.  Please post the output of:
> lspci

---

### Post by toshi.readman on 2007-09-28
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)

---

### Post by CaptainInsaneO on 2007-09-28
Do you have a livecd? If you run your livecd and it still does this, either your install CD is bad (which you can check for by running the "Check CD for defects" tool at startup) or your video controller is starting to die. But I really think it's probably your install that's bad, because you said your hardware worked fine under XP and 6.06. :)

---

