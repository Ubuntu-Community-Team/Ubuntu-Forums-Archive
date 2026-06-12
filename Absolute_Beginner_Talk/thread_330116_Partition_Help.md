---
title: "Partition Help"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by k1001001 on 2007-01-02
Hey guys. I was trying to do a dual-boot with Windows XP, however, the XP thing didn't work out because I didn't have my XP restore CD, and I needed a specific activation code which I didn't have apparently. To do this though, I had a partition in NTFS for Windows, however it was formatted and put back in ext3. Now I have this partition that I can't mount or really do anything with. Here's a screenshot of Qtparted:
[IMG]http://img.photobucket.com/albums/v62/k1001001/qtparted.png[/IMG]
hda1: Swap
hda2: Where Ubuntu is stored I believe (root folder)
hda3: Partition that is not working correctly (and strangely has files in it for some reason)
hda4: Extended (combines hda5 and hda6)
hda5: Home folder
hda6: Fat32 partition I had set up so I could use files on both Ubuntu and Windows (like for music)

Here's the Terminal output when I run qtparted:
```
keith@keith-laptop:~$ sudo qtparted
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
No Implementation: This ext2 file system has a rather strange layout!  Parted can't resize this (yet).
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.
```

And here's what happens when I try to mount hda3:
```
keith@keith-laptop:~$ sudo mount hda3
mount: can't find hda3 in /etc/fstab or /etc/mtab
```

Uh oh.

The guy who set all of this up put a folder in my home partition titled "NewPartition" and said that was the new partition, however I'm not sure it works like that. There's nothing in it at the moment.

So what I'm wanting to do is make use of this 5 GB just sitting there. How would I make this partition usable? Also, if it's possible, could I shove this partition in with my home partition or something to create more home file space? Thanks for any help!

---

### Post by k1001001 on 2007-01-02
Nevermind. I figured it out. I opened Nautilus, then unmounted and mounted the drive, then went back to the normal File Browser, and the partition worked then. Weird method, but it works.

---

