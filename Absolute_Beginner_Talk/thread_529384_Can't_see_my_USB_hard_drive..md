---
title: "Can't see my USB hard drive."
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by nesty on 2007-08-19
So I've got this external hard drive laying around with all my files that I wanted to keep saved over from Windows, but I can't seem to get it to show up in Ubuntu.

I had this same drive back in 6.06, and it was working fine then.

Apperantly 7.04 is recognizing it, but it still won't let me get to it.  I had my settings set to auto mount and auto open drives, but plugging my Maxtor hard drive in doesn't set off either of these, I can't find it on the desktop, nor anywhere else when I look through my files.  My camera card and other USB devices have all worked without a hitch, though.

What  can I do to see my stuff?

Here's some logs:

dmesg

```
[  138.996000] usb 2-2: new high speed USB device using ehci_hcd and address 7
[  139.156000] usb 2-2: configuration #1 chosen from 1 choice
[  139.156000] scsi3 : SCSI emulation for USB Mass Storage devices
[  139.156000] usb-storage: device found at 7
[  139.156000] usb-storage: waiting for device to settle before scanning
[  144.156000] usb-storage: device scan complete
[  144.192000] scsi 3:0:0:0: Direct-Access     Maxtor 6 L100P0           BAH4 PQ: 0 ANSI: 0
[  144.196000] SCSI device sdb: 195813072 512-byte hdwr sectors (100256 MB)
[  144.200000] sdb: Write Protect is off
[  144.200000] sdb: Mode Sense: 03 00 00 00
[  144.200000] sdb: assuming drive cache: write through
[  144.200000] SCSI device sdb: 195813072 512-byte hdwr sectors (100256 MB)
[  144.204000] sdb: Write Protect is off
[  144.204000] sdb: Mode Sense: 03 00 00 00
[  144.204000] sdb: assuming drive cache: write through
[  144.204000]  sdb: unknown partition table
[  144.216000] sd 3:0:0:0: Attached scsi disk sdb
[  144.216000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[  672.848000] FAT: invalid media value (0x10)
[  672.848000] VFS: Can't find a valid FAT filesystem on dev sdb.
```

lsusb:

```
Bus 002 Device 007: ID 0d49:3100 Maxtor 

```

ls /dev | egrep [hs]d

```

hda
ptysd
sda
sda1
sda2
sda5
sdb
ttysd
```

hdparm -I /dev/sdb

```
/dev/sdb:
 HDIO_DRIVE_CMD(identify) failed: Invalid argument

```

I included a bunch of other random stuff that a friend of mine I was talking to earlier about this issue asked for.  He said it might have something to do with libata but I don't know what that means! :confused:

Thanks everyone!  If there's any other info you need just ask.

---

### Post by bwtranch on 2007-08-19
I don't think I can provide anything useful. I have had USB problems with other devices hooked on the same bus. Could you possibly unhook everything else and re-boot to see if the HDD works? dmesg | less is a good thing to see what loaded at boot. I see you have done that and it does seem like the driver (module)  loaded. I was actually watching this thread to see if I could learn something. Maybe someone will come along. :lolflag:

---

### Post by mikeyphi on 2007-08-19
Just a thought - does your code:-

[  672.848000] VFS: Can't find a valid FAT filesystem on dev sdb.

look as though you can't see the drive because the filesystem has become corrupted?

---

### Post by msak007 on 2007-08-19
> **mikeyphi said:**
> Just a thought - does your code:-

[  672.848000] VFS: Can't find a valid FAT filesystem on dev sdb.

look as though you can't see the drive because the filesystem has become corrupted?

That's what I thought when I saw that message. I mean it *is *a Maxtor :-P (j/k). What filesystem was the drive formatted with? NTFS or ext3?

---

### Post by bwtranch on 2007-08-19
Re: #4 That is a good thought. Does anybody know the command to check that? I am in KDE right now and I feel lost. I am going to re-boot into Gnome. Gonna go back to Feisty, where I feel comfortable. See ya on the flip side :)

---

### Post by msak007 on 2007-08-19
> **bwtranch said:**
> Re: #4 That is a good thought. Does anybody know the command to check that? I am in KDE right now and I feel lost. I am going to re-boot into Gnome. Gonna go back to Feisty, where I feel comfortable. See ya on the flip side :)
Funny, I only feel at home using KDE. To each his own :)

Anyway if you want to check the filesystem of your hard drives, type this in a terminal:

```
sudo fdisk -l
``` (that's a lower case "L")

If it's ext2/3, it'll say "Linux" for the system. If it's NTFS, it'll say "HPFS/NTFS". For the OP, since he knows the drive is called sdb, he can just filter the results to get that one drive:

```
sudo fdisk -l | grep sdb
```

---

### Post by bwtranch on 2007-08-19
That's funny. I guess we get used to certain things. But, I LOVE KDE, it has a lot of programs that I like and Adept is cool. I am just trying to get used to things being on the bottom. And I have to install Firefox the first thing. Konqueor just doesn't do it for me. Ha! :)  Oh, it's all good. Anyway, I ran the command and here is the output for my machine:

jim@jim-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9405    75545631   83  Linux
/dev/hda2            9406        9729     2602530    5  Extended
/dev/hda5            9406        9729     2602498+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1328    10667128+   c  W95 FAT32 (LBA)
/dev/hdb2            2257        4865    20956792+   f  W95 Ext'd (LBA)
/dev/hdb3   *        1329        2256     7454160   83  Linux
/dev/hdb5            2301        2323      184716   82  Linux swap / Solaris
/dev/hdb6            2325        4865    20410551   83  Linux
/dev/hdb7            2257        2300      353367   82  Linux swap / Solaris

Partition table entries are not in disk order
jim@jim-desktop:~$ 

I just put this out for illistration and I don't have a problem at the moment. I am testing Gutsy in two instances. I don't really understand the first one FAT32, I thought I got rid of the windows part:confused:

---

### Post by nesty on 2007-08-19
> **mikeyphi said:**
> Just a thought - does your code:-

[  672.848000] VFS: Can't find a valid FAT filesystem on dev sdb.

look as though you can't see the drive because the filesystem has become corrupted?

That is a very real possibility.  I've had problems before with this hard drive in the past, although it was working just fine in Windows Vista.  I'll try and see if it'll show up on a family member's computer under Mepis sometime later today.

Here's the output from sudo fdisk -l | grep sdb:

> Disk /dev/sdb doesn't contain a valid partition table
Disk /dev/sdb: 100.2 GB, 100256292864 bytes


Not good! :(

---

### Post by msak007 on 2007-08-19
Definitely looks like either the filesystem was corrupted, or it was formatted and a new partition was not created and it's just blank space. I would try it in another Linux environment as you said you would, and in Windows if you have access to a comp with Windows on it. I'm not sure if Vista would've done anything to the hard drive to make it unreadable in other OSes. Wouldn't surprise me though...it does that with CDs burned through Explorer.

---

