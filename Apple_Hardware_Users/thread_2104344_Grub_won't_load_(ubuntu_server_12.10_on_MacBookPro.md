---
title: "Grub won't load (ubuntu server 12.10 on MacBookPro5,5)"
date: 2013-01-12
forum: Apple Hardware Users
---

### Post by minsf on 2013-01-12
Hi there, 

I'm trying to install ubuntu-**server**-amd64+mac ver 12.10 on a MacBookPro 5,5.
after installation, booting ubuntu hangs during grub.

the steps i have taken:

A) i installed refit 

B) i used diskutil to partition the drive as:
1) EFI partition - didn't touch it
2) mac's original HFS+ partition
3) ubuntu
4) another FAT partition used to transfer files between osx and ubuntu

C) i ran (server) install cd (i verified the checksum after downloading it and burned it with diskutil)

D) i have no swap and chose to simply install root (/) on /dev/sda3 (after formatting it with ext3)

E) i chose to not install grub to the mbr but rather to /dev/sda3

F) i re-synced the partitions with refit

now when choosing to boot from the "windows" partition (/dev/sda3) grub writes 
> GRUB
on the screen followed by a blinking cursor.

do i have to reinstall grub somehow?

---

### Post by almarphud on 2013-01-12
try tapping F12 on startup

---

### Post by minsf on 2013-01-12
> **almarphud said:**
> try tapping F12 on startup

thanks, but, unfortunately, pressing F12 does not change anything.
what am i supposed to get with F12?

---

### Post by minsf on 2013-01-13
Updates: 

I tried adding a small partition with a bios_grub flag and installing grub into it at the end of the installation. It seems that this flag causes rEFIt problems ("GPT partition of type 'Unknown' found, will not touch this disk."). When I simply remove that flag, rEFIt has no problem to sync my partitions anymore. 
Regardless, I get the same dark-gray/black screen with "GRUB" and a blinking cursor, both with bios_grub flag and without it (but with boot flag).

I also tried ubuntu desktop 12.04 amd64 (rather than the ubuntu server that I tried initially).
It fails with the same GRUB screen of death...

---

