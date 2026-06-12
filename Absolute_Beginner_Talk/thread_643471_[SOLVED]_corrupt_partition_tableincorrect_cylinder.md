---
title: "[SOLVED] corrupt partition table/incorrect cylinders after windows reinstall"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by johnnyoc3 on 2007-12-17
today i decided to install a fresh version of windows xp onto my internal laptop hd. before the installation the hd looked like this

```
sda1: a dell utility partition about 60mb
sda3: windows xp about 70gb
sda4:extended partiton
   sda5:ubuntu(ext3) about 10gb
   sda6:swap 3gb
   sda7:ext3(data) about 3gb
   sda8:freespace
```

sda5-8 were inside sda4 in gparted. if that makes any sense.

so now i previously created a bin backup of the MBR using

   ```
dd if=/dev/sda of=bootloader.bin count=512
```

install a new windows xp on sda8 and let windows format sda8 to ntfs and install its bootloader.
the computer restarts and i boot off a slax cd to restore my grub bootloader using

   ```
dd if=/path/to/bootloader.bin of=/dev/sda

```
i reboot and grub gives me an error 15 or 17. i cant remember but it didnt make it past stage 1

so i put in my windows xp cd and used fixmbr from the repair console

now i reboot and niether the old windows (sda3) or the new windows boots.
the new windows give me a BSOD during bootup saying: ```
UNMOUNTABLE VOLUME (0x0.....ED)
```
the old windows (sda3) doesnt boot up at all

i booted slax again and ran 

   ```
sudo fdisk -l
```

it says:

```
[FONT="Times New Roman"]   Warning: ignoring extra data in partition table 5
   Warning: ignoring extra data in partition table 5
   Warning: invalid flag 0x6800 of partition table 5 will be corrected by w(rite)

   Disk /dev/sda: 120 GB, 120034123776 bytes
   255 heads, 63 sectors/track, 14592 cylinders
   Units = cylinders of 16065 * 512 = 8225290 bytes

Device boot Boot     Start        End             Blocks         Id          System
   /dev/sda1                 1             6             48163+         de        Dell Utility
   /dev/sda2      *         7        1311      10482412+          7         HPFS/NTFS
   /dev/sda3           1312      13376      96907264             7         HPFS/NTFS 
   Partition 3 does not end on cylinder boundry
   /dev/sda4         13377      14594        9776577+          f          W95 Ext'd (LBA)
   Partition 4 does not end on cylinder boundry
   /dev/sda5      ?  13374    157270  1155842815+         ff         BBt
[/FONT]
```
also. chkdsk(off of winXP cd) says "one or two unrecoverable errors" and
```

   fsck /dev/sda
   Couldn't find ext2 superblock, trying backup blocks...
   /sbin/e2fsck: Bad magic number in super-block while trying to open /dev/sda

   The superblock could not be read or does not describe a correct ext2 filesystem. 
   .........
   ...a bunch of suggestions here....
   ........
```

at this point i would just like to recover my files to a usb drive. as of the current partition table i can only mount sda1 successfully. if there is some way to fix the partion table that would be great.

any help is appreciated

---

### Post by Sef on 2007-12-17
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by johnnyoc3 on 2007-12-17
test disk worked great and restored my partition table :)

thanks a bunch.

---

