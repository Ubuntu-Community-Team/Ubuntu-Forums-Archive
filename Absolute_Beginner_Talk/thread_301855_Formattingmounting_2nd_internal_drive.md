---
title: "Formatting/mounting 2nd internal drive"
date: 2006-11-17
forum: Absolute Beginner Talk
---

### Post by dnschneider on 2006-11-17
I've installed Ubuntu on a Mac G4, which has 2 internal drives. This is an older computer, and I have no need to have the Mac OS on it, so it's to be totally dedicated to Ubuntu. One of the drives, obviously, was formatted by the installer and has the Ubuntu OS installed on it. I would like to have access to the second internal drive, but I'm a little unclear how to access it within linux. I can see it in the Device Manager, but I'm not sure what to use to format/mount it. 

As you can probably tell, I'm brand new to linux, so please use small words. :D

---

### Post by taurus on 2006-11-17
Open a terminal, Applications -> Accessories -> Terminal, and paste the following command here.

```
sudo fdisk -l
```

---

### Post by dnschneider on 2006-11-17
Okay, did that. This is what it responded with:


/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               1954 @ 64       (977.0k)  NewWorld bootblock
/dev/hda3         Apple_UNIX_SVR2 untitled           19169922 @ 2018     (  9.1G)  Linux native
/dev/hda4         Apple_UNIX_SVR2 swap                 894311 @ 19171940 (436.7M)  Linux swap

Block size=512, Number of Blocks=20066251
DeviceType=0x0, DeviceId=0x0

/dev/hdd
        #                    type name                 length   base     ( size )  system
/dev/hdd1     Apple_partition_map Apple                    63 @ 1        ( 31.5k)  Partition map
/dev/hdd2              Apple_Boot eXternal booter       17408 @ 64       (  8.5M)  Unknown
/dev/hdd3               Apple_UFS Apple_UFS_Untitled_1 39858992 @ 17472    ( 19.0G)  Unknown
/dev/hdd4              Apple_Free                          16 @ 39876464 (  8.0k)  Free space

Block size=512, Number of Blocks=39876480
DeviceType=0x0, DeviceId=0x0

---

