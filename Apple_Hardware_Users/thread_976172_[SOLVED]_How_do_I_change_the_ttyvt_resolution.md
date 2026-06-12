---
title: "[SOLVED] How do I change the tty/vt resolution"
date: 2008-11-09
forum: Apple Hardware Users
---

### Post by hanzomon4 on 2008-11-09
The text in my tty/vt consoles are too big. How do I change the resolution to 1440x900?

macbook pro v3.1
8.10 ubuntu

---

### Post by bryonak on 2008-11-09
A quick trip to the search function reveals [this thread]("http://ubuntuforums.org/showthread.php?t=122936").

---

### Post by hanzomon4 on 2008-11-09
Thanks I got it by installing hwinfo and running "hwinfo --framebuffer". then adding vga=0x0365. I knew how to do it I just could not find the right vga=XxXXX parameter.

---

### Post by cyberdork33 on 2008-11-09
I made a table of all the values here:
[http://www.rickycampbell.com/table-of-framebuffer-resolution-values/](http://www.rickycampbell.com/table-of-framebuffer-resolution-values/)

---

### Post by hanzomon4 on 2008-11-09
That's actually not all of them your chart leaves out a few including the one for my screen 1440x900.

Here is a list of all the modes for the macbook pro 3.1 ```
 sudo hwinfo --framebuffer
[sudo] password for qbradf: 
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.450]
  Unique ID: rdCR.U6_RKFsqv18
  Hardware Class: framebuffer
  Model: "NVIDIA GeForce 8600M GT    "
  Vendor: "NVIDIA Corporation"
  Device: "GeForce 8600M GT    "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 14 MB
  Memory Range: 0x91000000-0x91dfffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown



```

I used vga=0x0364

---

### Post by cyberdork33 on 2008-11-09
Yes, I leave out several. I tried to just do the more common ones. VESA only defines up to 1280x1024, but I put UGA on there because it is one standard (4:3) size up from 1280x1024, and there are a lot of high resolution capable cards/monitors out there now.

there are ALOT more out there depending on your situation:
[http://en.wikipedia.org/wiki/VESA_BIOS_Extensions](http://en.wikipedia.org/wiki/VESA_BIOS_Extensions)

---

