---
title: "Xorg Kernel Panic"
date: 2009-11-08
forum: Apple Hardware Users
---

### Post by techweenie1 on 2009-11-08
I've been having this problem ever since I tried installing Ubuntu on my old Power Mac G4 since the beginning, I think the first version I tried it with was 7.04.  I tried installing it again with 9.10 but again same problems.  Basically what happens is after booting into X with the Live CD after a few short minutes the system completely locks up, can't switch to virtual console using ctrl+alt+Fn key, or the screen goes black and says "out of range," I've tried this on multiple monitors.

I remember using the alternative install CD to install 7.04, but once everything was installed, I was having the same problems, until I switch the video driver to vesa or something without 3D acceleration enabled, which is not something I want to do.  I have a Radeon 8500 Mac Edition (64 mb) are there any drivers anyone can suggest I use before I download the alternative install of 9.10?

Here are my basic specs

Power Macintosh G4 (AGP)
Original Processor G4 @ 400mhz, Upgraded it to G4 @ 1.4 ghz
Radeon 8500 Mac Edition (64mb)
512 mb RAM

---

### Post by techweenie1 on 2009-11-11
Well I ended up setting "DRI" "false" in my xorg.conf file, kind of sucks that I can't have all the fancy eye candy, anyone have any ideas on a driver out there that works for the Radeon 8500 and allows for stable DRI?

---

