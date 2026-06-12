---
title: "Debian Squeeze v6.0.2.1 - Backlit Keyboard"
date: 2011-08-30
forum: Any Other OS
---

### Post by AdamShumpisxXx on 2011-08-30
I'm hoping I'm posting this in the correct thread. I noticed the main threads are specifically limited to *buntu variants and this is more open to Linux in general. Anyways, on with the dilemma...

I have a Toshiba Satellite A665D-S6091 Laptop. In Windows (7 Ultimate x64 SP1) the keyboard backlight works as intended. I have tried the "Always On" function in BIOS to no avail. Most solutions given apply only to Macintosh based laptops and certain ASUS based laptops but none have worked with me. From what I gather it seems to be an ACPI issue. To be honest, I'd like to ditch Windows for EVERYTHING other than gaming and certain design applications but this function is really holding me back. I know it may not seem much to some but for me the backlight is a necessity when working in my usually dark work spaces / when I'm just laying back watching YouTube.

For those wondering...Go Debian. You'll not find a better version of Linux. I used to ride the Ubuntu train since 7.10 but once I tried Debian, so many base problems just melted away. Just for those who are on the fence. You will NOT be disappointed.

---

### Post by NightwishFan on 2011-08-30
I will post some chunks of information as I do not know the solution.

[http://ubuntuforums.org/showthread.php?t=1533744&page=2](http://ubuntuforums.org/showthread.php?t=1533744&page=2)
> If ACPI is disabled in kernel boot line, the keyboard backlight work. Even Fn+y key combination work - to enable/disable backlight. 
 The problem with ACPI disabled is that anything other then keyboard backlight, sound volume and mute don't work and OS can't detect all 8 cores (4*2 hiperthreaded).

Can test if this is true by appending the following to grub temporarily (at boot time).
```
acpi=off
```
**********

> I have an A665-6065 and had the same issue where the keyboard is not backlit and the controls near the power button don't work. I recently installed Windows 7 on my computer in a dual-boot configuration, and I discovered that if I suspend my current Windows session and reboot into Ubuntu, the keyboard is backlit and the controls are working! If I shut down Windows and reboot into Ubuntu, the keyboard isn't backlit and the controls don't work. I can only speculate about this "phenomenon" although I suspect it's BIOS-related....?
**********

[https://bugzilla.kernel.org/show_bug.cgi?id=32742](https://bugzilla.kernel.org/show_bug.cgi?id=32742)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683133](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/683133)
**********

Seems like no fix yet?

---

### Post by AdamShumpisxXx on 2011-08-30
I've heard rumblings about the newest firmware having the capability. No idea. :( I really would love to ditch as many uses as I can on my Windows partition.

---

### Post by NightwishFan on 2011-08-30
You can try building kernel 3.0 perhaps. .39 is in backports 3.0 will probably be soon though.

---

