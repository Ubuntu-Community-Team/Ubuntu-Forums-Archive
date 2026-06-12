---
title: "BackTrack Error"
date: 2012-02-21
forum: Any Other OS
---

### Post by Draksis on 2012-02-21
When shutting down BackTrack 5 R1 (Ubuntu 10.04 based distro), I get this error:

```
EXT2-fs (sdb2) error: ext2_lookup: deleted inode referenced
```

Initially, I was able to ignore this. However, over time, my files began doing funny things. Some folders wouldn't be able to be modified (some I/O error I can't recall; I can post it if needed), and eventually X wouldn't start.

I am running BT5 off of a persistent USB drive. I have tried reinstalling to different flash drives numerous times, and the issue persists. Does anyone know what I can do to fix it?

EDIT: BTW, I'm not sure if this is "all variants". If it isn't, just tell me, and I'll fix it.

---

### Post by Draksis on 2012-02-22
Update/bump: I tried installing BT on multiple other USB drives and used an EXT3 partition instead of EXT2, but the problem persists.

Any clue what is wrong? I have seen numerous posts about this issue on the internet, but no working suggestions on how to fix it.

---

### Post by backtracking on 2012-06-01
Same problem here.

First I used universal usb installer 1.8.9.9. to create a bootable backtrack usb stick (8GB). I set persistent memory to 2299 MB or so. 

BT5 BTR1 and BT5R2 (< all KDE 32bit) all damage the casper-rw file on the very first shut down -h 0.


Then I tried making the usb-stick by loading the iso's in VMware and partition the stick directly from the konsole (fdisk /dev/sdb1), making a FAT32 (2.5GB) partition and an EXT3 (rest of stick).

At the very first shutdown -h 0, I get several I/O errors...

---

