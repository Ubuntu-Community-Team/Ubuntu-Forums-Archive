---
title: "how to get bluetooth dongle working?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by jinxjinx on 2006-08-24
Hi, I just bought a Think Outside stowaway bluetooth keyboard but im not sure why it wont work...

when i run hcitool scan i get this:
~/.cairo-dock$ hcitool scan
Scanning ...
        00:16:38:EC:27:0D       Think Outside Keyboard

then if i run hidd --search:
:~/.cairo-dock$ sudo hidd --search
Searching ...
        Connecting to device 00:16:38:EC:27:0D

and if i do hidd --show:
~/.cairo-dock$ hidd --show
00:16:38:EC:27:0D Broadcom Corp. Keyboard [0a5c:2001] connected 


but i still cant type with it...
any thoughts??

Thanks


never mind guys got it to work with this: [http://www.ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+keyboard](http://www.ubuntuforums.org/showthread.php?t=227057&highlight=bluetooth+keyboard)

---

