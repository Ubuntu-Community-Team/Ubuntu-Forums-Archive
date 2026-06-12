---
title: "GParted won't resize ext3 partition on external drive"
date: 2007-09-19
forum: Apple PPC Users
---

### Post by ubuntubrian on 2007-09-19
I bought a new drive for my TiBook-dual boot- and successfully cloned all my partitons on the TiBook to it by installing it into a USB case and doing it remote.
Now I want to grow my Linux partition to use some of the 60GB of free space. The swap partition was between the ext3 linux partition and the free space so I moved it and now have on the USB drive:

Using /dev/sda
(parted) print
Disk geometry for /dev/sda: 0kB - 120GB
Disk label type: mac
Number  Start   End     Size    File system  Name                  Flags
1       1kB     32kB    32kB
2       33kB    65kB    33kB                 Macintosh
3       66kB    98kB    33kB                 Macintosh
4       98kB    360kB   262kB                Patch Partition
5       360kB   43GB    43GB    hfs+         Macintosh HD
6       43GB    43GB    1000kB               untitled              boot
7       43GB    43GB    1000kB  hfs          untitled              boot
8       43GB    59GB    16GB    ext3         untitled
9       96GB    97GB    734MB   linux-swap   swap                  swap

I( found out from MicroMat that those little partitions are Apple's work around of a problem that I don't understand) 
And:
sudo fdisk -l /dev/sda
/dev/sda
        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map                           63 @ 1         ( 31.5k)  Partition map
/dev/sda2        Apple_Driver_ATA Macintosh                 64 @ 64        ( 32.0k)  Unknown
/dev/sda3        Apple_Driver_ATA Macintosh                 64 @ 128       ( 32.0k)  Unknown
/dev/sda4           Apple_Patches Patch Partition          512 @ 192       (256.0k)  Unknown
/dev/sda5               Apple_HFS Macintosh HD        84062256 @ 704       ( 40.1G)  HFS
/dev/sda6         Apple_Bootstrap untitled                1954 @ 84062960  (977.0k)  NewWorld bootblock
/dev/sda7         Apple_Bootstrap untitled                1954 @ 84064914  (977.0k)  NewWorld bootblock
/dev/sda8         Apple_UNIX_SVR2 untitled            31722657 @ 84066868  ( 15.1G)  Linux native
/dev/sda9         Apple_UNIX_SVR2 swap                 1433601 @ 188163797 (700.0M)  Linux swap
/dev/sda10             Apple_Free Extra               72374272 @ 115789525 ( 34.5G)  Free space
/dev/sda11             Apple_Free Extra               44844250 @ 189597398 ( 21.4G)  Free space

Gparted shows the Linuxswap in between the sda10 and 11above. See screenshot-maybe:
[IMG]file:///home/brianokeefe/Desktop/Gparted.png[/IMG]

When I unmount the partitions (doing this from my boot drive to the USB drive) and select "resize/move" for sda8 and grow it to take up the first free space and apply the changes 2 things happen. The partition remounts itself along with the boot and swap partitions and then Gparted gives me an error that I have tried perform an operation on a mounted partition.
The result is that the partition won't grow and Gparted freaks-last night it showed the whole drive as unallocated space but upon start up this AM I get what you see above.
Here's what I want to do and Gparted is ready to apply changes but then gives me the error described above:

[IMG]file:///home/brianokeefe/Desktop/Screenshot.png[/IMG]

Hope these screenshots work.
Many thanks

---

### Post by ubuntubrian on 2007-09-19
Sorry the screenshots didn't post and I don't know how to post them so hopefully the text suffices.
Thanks

---

### Post by ubuntubrian on 2007-09-19
I'm creating my own thread I guess.
I reran Gparted and the partition was resized from 15GB to 53GB. However, the unused space stayed the same at 3.5GB! Wha.......

The directories all appear normal and din't multiply or anything that I know of so any ideas?
Thanks

:lolflag:

---

### Post by pxwpxw on 2007-09-20
> **ubuntubrian said:**
> I'm creating my own thread I guess.
I reran Gparted and the partition was resized from 15GB to 53GB. However, the unused space stayed the same at 3.5GB! Wha.......

The directories all appear normal and din't multiply or anything that I know of so any ideas?
Thanks

:lolflag:

Hi,

If you still have a problem,  post an updated fdisk listing for the external and another for the internal drive and also: 
```

 cat /etc/fstab

```

---

### Post by ubuntubrian on 2007-09-20
I may have solved it. Checking with Gparted forums I found enough similar issues that I did a tweak. I re-ran Gparted and shrank the partition in question by 250kb. apparently this "bumps" Gparted's detection and when done the partition was correct, unused space and all.
Also found out that the "unallocated" space that shows up after running Gparted acroos the entire drive resets to the real values upon rebooting or disconnecting and reconnecting a remote (like the one I'm working on) drive.
Thanks for the input!

:)

---

