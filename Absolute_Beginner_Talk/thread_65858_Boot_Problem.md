---
title: "Boot Problem"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by Sputnikmercromínic on 2005-09-15
First of all, I'd like to apologise if this turns out to be some stupid question which has been asked around 7380437803703 times... but, anyway, I've read documentation, how-tos and looked around the forum without finding an answer, so I'll post it anyway. Well, before explaining the problem itself, I guess I should describe how my partitions are, as this is a question about this kind of stuff...
Before installing Ubuntu, I basically had three partitions on two hard disks, which means a FAT partition and a NTFS on one of the hard disks, and just a single NTFS partition on the other one. I had two operative systems set up on the first drive, that is, Win 95 on the FAT partition, and Win XP on the NTFS one. So then I installed Ubuntu by formatting the FAT partition as an EXT3 one, and then I chose GRUB as the boot manager and overwrote the MBR with it, which boots Ubuntu just fine. Problem is, I have edited the GRUB menu list file so that it boots Win XP, but I guess I kind of screwed up, since it actually doesn't. What I have put on the file is as follows:


```
title		Windows XP 
map (hd0,0) (hd0,1)
map (hd0,1) (hd0,0)
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
```

I have also tried doing the same with (hd0,4), since it's hdc5 what I can mount on Ubuntu (trying hdc2 seems to crash the system just about always, hehehe), and even (hd1,4) and (hd,1,0) and (hd1,1), and also removing the map thing as I guessed it was some outdated old Windows thing, but all I get is the same message: upon running makeactive, GRUB says "invalid device requested". So, anyway, perhaps this means I kind of destroyed the Windows boot or something like that, doesn't it? That'd be kind of strange, too, because it turns out I can actually mount the NTFS partitions on Ubuntu and read them and stuff, so I don't really know. Could anybody please help me?

EDIT: Oh! I almost forgot! I had some problems installing GRUB. The first time I tried to set it up it failed to install, so I told the Ubuntu installer to install LILO instead, but the system wouldn't boot, so I had to reinstall Ubuntu, and that time GRUB worked fine with Linux, but not with Windows, as I have said.

---

### Post by Kapre on 2005-09-15
```
title		Windows XP 
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
```

EDIT: Oh! I almost forgot! I had some problems installing GRUB. The first time I tried to set it up it failed to install, so I told the Ubuntu installer to install LILO instead, but the system wouldn't boot, so I had to reinstall Ubuntu, and that time GRUB worked fine with Linux, but not with Windows, as I have said.[/QUOTE]

sputnik - Try removing the map so it would look like the one above. If that's been tried, and you want to boot into windows try getting a windows 98 boot floopy and boot from it. At the prompt type in fdisk /mbr so it would fix it. After that you will be able to boot in windows but not in linux. Then you have to reinstall the grub (use the live cd)

EDIT: [This](http://www.ubuntuforums.org/showthread.php?t=65392&highlight=grub+reinstall) will help you on editing/reinstalling the grub

---

### Post by Sputnikmercromínic on 2005-09-15
Well, editing the menu list file doesn't seem to work, so I'll just have to do what you said and reinstall GRUB afterwards... I'll try to get some boot disk which can read NTFS drives, because all the ones I have are Win95 or even MS-DOS disks... thanks a lot for your help! :)

---

