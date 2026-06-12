---
title: "Dual booting on a 800mhz iBook G4"
date: 2009-12-07
forum: Apple Hardware Users
---

### Post by nekobrain on 2009-12-07
Hi everybody, this is my first post here. I'm not a total newbie with Ubuntu, on my desktop I've had a dual boot system for a few years, but I'm stuck with my iBook G4. 

I wanted to try Ubuntu there too, so what yesterday I defragmented my MacOSX partition and shrank it to make space for Ubuntu. No problems whatsoever, MacOS boots just fine. The thing is, when I try to install Ubuntu from the Live CD (8.04.1 version) the installer doesn't see the partition where MacOS is installed. I tried Partition Manager from the Admin tools, too, with no luck. These two programs see the entire 27gb of my HDD as "undefined", not recognizing any partition. 

What should I do? I'd prefer not to lose anything and not to re-format and re-partition the entire HDD...

Thanks in advance for your help, guys!

EDIT:

This is the output of sudo fdisk -l, hope it helps!

```
ubuntu@ubuntu:~$ sudo fdisk -l
/dev/hda
        #                    type name                 length   base     ( size )  system
/dev/hda1     Apple_partition_map                          63 @ 1        ( 31.5k)  Partition map
/dev/hda2         Apple_Bootstrap untitled               2048 @ 64       (  1.0M)  NewWorld bootblock
/dev/hda3               Apple_HFS Macintosh HD       46574272 @ 2112     ( 22.2G)  HFS
/dev/hda4              Apple_Free                    12028736 @ 46576384 (  5.7G)  Free space

Block size=512, Number of Blocks=58605120
DeviceType=0x0, DeviceId=0x0

/dev/hdc
        #                    type name                length   base    ( size )  system
/dev/hdc1     Apple_partition_map Apple                    2 @ 1       (  1.0k)  Partition map
/dev/hdc2               Apple_HFS Ubuntu 8.04.1 ppc  1392104 @ 16      (679.7M)  HFS

Block size=512, Number of Blocks=1392120
DeviceType=0x1, DeviceId=0x1
```

---

