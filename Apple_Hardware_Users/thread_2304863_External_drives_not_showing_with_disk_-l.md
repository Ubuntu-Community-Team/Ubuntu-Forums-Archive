---
title: "External drives not showing with disk -l"
date: 2015-11-30
forum: Apple Hardware Users
---

### Post by tiago_ferreira2 on 2015-11-30
Hi, I have an Apple PowerBook G4 (2004), with a PowerPC processor, running ubuntu server 14.04 LTS. I have already tried with multiple drives, cables, ports, the drives won't show up with disk -l but I can identify them perfectly with lsusb.

Without drive:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:020f Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 002 Device 002: ID 05ac:1000 Apple, Inc. Bluetooth HCI MacBookPro (HID mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

With drive:

```
Bus 001 Device 062: ID 1058:1042 Western Digital Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:020f Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 002 Device 002: ID 05ac:1000 Apple, Inc. Bluetooth HCI MacBookPro (HID mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```


Also, when I use disk -l, I get this:

```


    There is a valid Mac label on this disk.
    Unfortunately fdisk(1) cannot handle these disks.
    Use either pdisk or parted to modify the partition table.
    Nevertheless some advice:
    1. fdisk will destroy its contents on write.
    2. Be sure that this disk is NOT a still vital
       part of a volume group. (Otherwise you may
       erase the other disks as well, if unmirrored.)




Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


   Device Boot      Start         End      Blocks   Id  System



```

But if I use mac-fdisk -l:

```
/dev/sda        #                    type name                  length   base      ( size )  system
/dev/sda1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/sda2         Apple_Bootstrap untitled                1954 @ 64        (977.0k)  NewWorld bootblock
/dev/sda3         Apple_UNIX_SVR2 untitled           149841797 @ 2018      ( 71.5G)  Linux native
/dev/sda4         Apple_UNIX_SVR2 swap                 6457624 @ 149843815 (  3.1G)  Linux swap
/dev/sda5              Apple_Free Extra                     49 @ 156301439 ( 24.5k)  Free space


Block size=512, Number of Blocks=156301488
DeviceType=0x0, DeviceId=0x0



```

---

### Post by rican-linux on 2015-12-02
what does lsblk show?

---

### Post by tiago_ferreira2 on 2015-12-02
The code doesn't changes when I add or remove the drive:



NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0  74.5G  0 disk 
&#9500;&#9472;sda1   8:1    0  31.5K  0 part 
&#9500;&#9472;sda2   8:2    0   977K  0 part 
&#9500;&#9472;sda3   8:3    0  71.5G  0 part /
&#9500;&#9472;sda4   8:4    0   3.1G  0 part 
&#9492;&#9472;sda5   8:5    0  24.5K  0 part 
sr0     11:0    1  1024M  0 rom

---

### Post by rican-linux on 2015-12-03
is your drive USB 3.0?

---

### Post by tiago_ferreira2 on 2015-12-03
Yes, but I think it is 2.0 compatible.

---

### Post by rican-linux on 2015-12-05
I am having the same issue on my iBook G4. It will not read USB 3.0 devices. You may be out of luck with that one.

---

### Post by tiago_ferreira2 on 2015-12-05
Ah damn it!
Because what I don't understand is why does it appears with lsusb but I'm unable to mount it! And I have used this drive with the previous OS X 10.5 on this mac and it worked perfectly! So it's defenatley a software bug on the os.

---

### Post by rsavage on 2015-12-27
> **rican-linux said:**
> I am having the same issue on my iBook G4. It will not read USB 3.0 devices. You may be out of luck with that one.
No problem here with a new seagate backup drive I've got.

---

### Post by tiago_ferreira2 on 2015-12-27
Is it USB 3.0 or 2.0? I had to use an USB 2.0, the 3.0 don't seem to work :(

---

### Post by rsavage on 2015-12-27
This one [http://www.seagate.com/gb/en/products/laptop-mobile-storage/laptop-external-drives/backup-plus-slim-mac/#features](http://www.seagate.com/gb/en/products/laptop-mobile-storage/laptop-external-drives/backup-plus-slim-mac/#features)

---

