---
title: "Problem booting from Live CD"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by The End on 2006-05-10
Hi everyone,

I'm a n00b when it comes to Linux so I'm not really sure what's going on here.

I'm having trouble booting from the Live CD I burned from an ISO. The Disc itself is fine and works properly since I was able to run it with no problems on my desktop, but getting it to work with my notebook is giving me some trouble.

Whenever I try to boot on this notebook it displays my MAC address, begins to load, then it stops and gives me the following error:

[B]PXE-E53 no boot filename recieved

Exiting ROM[/B]


It then loads into windows. 

I'm running the following:

Processor: Intel Pentium M Processor 750 (1.86 GHz, 2 MB L2 Cache, 533 MHz FSB)
Operating System: Microsoft Windows XP Home
System Chipset: Mobile Intel 915GM Express Chipset
Graphics Controller: Intel Graphics Media Accelerator 900 (128 MB shared VRAM) graphics processor
Memory: 1024 MB (standard) PC2700 DDR333 SDRAM memory
Hard Drive: 100 GB (5400 rpm) HDD
Optical Drive: DVD SuperMulti Double Layer drive
Wireless: Intel Pro/Wireless 2200BG (802.11b/g)


Any help is appreciated.

---

### Post by barbarian on 2006-05-10
Hi,
try to burn on slower speed, perhaps..

---

### Post by The End on 2006-05-10
[QUOTE=barbarian]Hi,
try to burn on slower speed, perhaps..[/QUOTE]


I burned the ISO at 4x

---

### Post by adam.tropics on 2006-05-10
It looks to me more like it's trying to do a network boot, rather than booting from the cd itself, hit F10 (or whatever your laptop requires for either one off boot options (I have that with toshiba) or bios), and the n make sure it is set to boot from cd....(ps, there's alot on this if you google PXE-E53)

---

### Post by barbarian on 2006-05-10
+1
> PXE-E53 no boot filename received

Exiting ROM

Yes it looks like computer try to boot from network. You, probably, should change boot sequence in BIOS.

---

### Post by The End on 2006-05-10
[QUOTE=barbarian]+1


Yes it looks like computer try to boot from network. You, probably, should change boot sequence in BIOS.[/QUOTE]


My boot sequence is as follows when the problem occurs:

CD-ROM > LAN > FDD > HDD

CD-ROM boot being first.

---

### Post by barbarian on 2006-05-11
Which program you used for burning? Nero? If so You should select option - burn ISO like an image not like data CD. You computer skips CDROM when booting. If it's brand new the most likely, ISO burned with wrong parameters, IMHO

---

### Post by confused57 on 2006-05-11
Is your CD drive spinning up to speed when trying to  boot the LiveCD, some high speed CD drives take so long getting up to speed the Bios skips to the next boot device?  Have you tried rebooting with the LiveCD  inserted in your CD drive?
For some reason, your Bios isn't recognizing the LiveCD in your drive, as if you didn't probably already conclude that.

---

### Post by The End on 2006-05-11
I'm staring to think it might be a problem with the drive itself since I am now having trouble reading install CDs while in Windows.

---

