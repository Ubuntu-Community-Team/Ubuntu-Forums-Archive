---
title: "Boot error"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Mr.Kuchinawa on 2007-01-10
When I try to boot the live cd, I select "boot from cd", and so the loading screen appear. After about 3 minutes, somethng like this appear: "expected null handler on exit"

I tested the same cd on another PC, and it worked just fine. What is wrong?

Thanks in advance

---

### Post by kebes on 2007-01-10
Could be a hardware issue. If you post the exact specs of the machine you're trying to boot on, someone may recognize the issue. Often times there are known bugs or workarounds.

---

### Post by Mr.Kuchinawa on 2007-01-10
I don't exactly know wich spec's you're interested in, but here's some:

Intel Pentium 4 CPU 3.00GHz 

Motherboard: Asus P4S800-MX (3 PCI, 1 AGP, 2 DDR DIMM, Audio, Video, LAN) 

Motherboard chipset: SiS 661FX 

1024 Mb (PC3200 DDR SDRAM) 

BIOS type: AMI (09/01/04) 

NVIDIA GeForce 6600 GT (128 Mb) 

HDS722516VLAT80 (160 Gb, 7200 RPM, Ultra-ATA/100) 

It's an Asus....

---

### Post by kebes on 2007-01-10
Hmm... I don't see anything on your hardware list that would cause a problem. Other things to try:

1. You said the CD worked on other computers, so it's probably fine, but doing a CD check wouldn't hurt. Perhaps use the CD to do a memtest, too.

2. You could also try other versions of Ubuntu. For instance, you could try booting the Dapper instead of Edgy LiveCD and see if that makes a difference.

3. Also see this thread:
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

Some people report that unplugging USB devices solves the problem. Other potential solutions are also mentioned.

4. This post:
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)

summarizes other things to try when seeing that error.


Hope that helps.

---

### Post by Modernity on 2007-01-10
> **kebes said:**
> Hmm... I don't see anything on your hardware list that would cause a problem. Other things to try:

2. You could also try other versions of Ubuntu. For instance, you could try booting the Dapper instead of Edgy LiveCD and see if that makes a difference.



Try Dapper LiveCD and see if you can get it to boot.

---

