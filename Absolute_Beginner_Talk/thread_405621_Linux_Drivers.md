---
title: "Linux Drivers?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by Travelerr on 2007-04-10
So, here's my setup. I am on a Gateway MX3416 Notebook. 

OS - Edgy Eft 6.10

Processor - AMD Turion 64 Mobile Technology MK-36 # 2.0 GHz, 512Kb L2 Cache

Video / Audio - nVidia Geforce Go 6100 with 128MB Turbocache

I've got almost everything working correctly, but I have no video driver and absolutely no sound. Here is a website that contains the XP / Vista drivers of what I need, if that helps at all...

```
http://www.drivershq.com/Drivers/Gateway/Notebook-Computer/Gateway-MX3416/9771/23769/25318/Drivers.aspx
```

Any help would be awesome.

---

### Post by moffa on 2007-04-10
The nvida driver package is called nvidia-glx.
I have the same sound card on my laptop and it worked out of the box.  Try checking the channels and make sure nothing is muted

---

### Post by Travelerr on 2007-04-10
It's still not playing anything, and I can't find anything muted.

---

### Post by freebird54 on 2007-04-10
OPen a terminal, type in  alsamixer.  Set EVERYTHING up to at least 65%.  Try again.  Even settings that can't apparently have any effect - seem to!

---

### Post by jido on 2007-04-10
in a bash console, type:

[prompt] $ sudo apt-get install nvidia-glx


check what sound card is: 

[prompt] $ lspci

And load the convenient driver by:  

[prompt] $ sudo modprobe <module>

example: try: modprobe snd-intel8x0

However, it should work out of the box.

-------

---

