---
title: "Round 1:  Making NTFS partition writable"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by casaba on 2007-07-28
Okay, some real 'absolute beginner' questions:

My problems relate to mounting and accessing hard drives.  I have a dual boot machine with two IDE HDs, the first has two partitions, one for Windows/programs  and a second for 'Storage', both formatted NTFS.   (The second internal HD is dedicated to Ubuntu with default partitions.)  I would like to get read-write access for the Storage partition.  

I installed the ntfs-config package, and it's dependents and my etc/fstab file now includes:

/dev/sda1 /media/storage ntfs-3g defaults,locale=en_GB.UTF-8 0 0

However, nothing much has changed; I still have read access to Storage but not write access.  (Oddly, the Windows partition, which had the same read-only access before, now cannot even be mounted because "You are not privileged to mount this volume"?)


And my second related problem is mounting an external USB hard drive, also NTFS.  I added the following to etc/fstab:

/dev/sdd1 /mnt/USB auto noauto,user,kuzu 0 0

The error I get when trying to mount the USB drive is:

Unable to mount the selected volume.  The volume is probably in a format that cannot be mounted.
mount:wrong fs type, bad option, bad superblock on /dev/sdd1, missing codepage or other error
in some cases useful info is found in syslog - try dmesg | tail or so

(This, like most of what I have tried over the last two days, was gleaned off numerous Ubuntu and Linux help sites.  The 'sdd1' was found in the following 'dmesg':

[  190.106638] NTFS volume version 3.1.
[  433.920195] usb 2-1: new full speed USB device using uhci_hcd and address 3
[  437.710726] usb 2-1: configuration #1 chosen from 1 choice
[  437.962657] scsi3 : SCSI emulation for USB Mass Storage devices
[  437.962901] usb-storage: device found at 3
[  437.962906] usb-storage: waiting for device to settle before scanning
[  443.756000] usb-storage: device scan complete
[  444.511727] scsi 3:0:0:0: Direct-Access     HDS72808 0PLAT20          PF2O PQ: 0 ANSI: 0
[  445.771876] SCSI device sdd: 160836480 512-byte hdwr sectors (82348 MB)
[  447.030709] sdd: Write Protect is off
[  447.030721] sdd: Mode Sense: 03 00 00 00
[  447.030725] sdd: assuming drive cache: write through
[  448.290746] SCSI device sdd: 160836480 512-byte hdwr sectors (82348 MB)
[  449.550178] sdd: Write Protect is off
[  449.550191] sdd: Mode Sense: 03 00 00 00
[  449.550194] sdd: assuming drive cache: write through
[  449.550205]  sdd: sdd1
[  450.305839] sd 3:0:0:0: Attached scsi disk sdd
[  450.305921] sd 3:0:0:0: Attached scsi generic sg4 type 0

Please feel free to over-explain any silly mistakes here as I am rather lost on the syntax of the lines that I've added to fstab.)

Thanks in advance,
Casaba

---

### Post by aysiu on 2007-07-28
Try [this](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html).

---

### Post by Kent84 on 2007-07-28
I used Automatix to get my NTFS partitions writable on 3-4 different machines and it worked fine. Note Automatix is not officially supported...

---

### Post by kelvin spratt on 2007-07-28
I had trouble mounting my USB Drive this is my Fstab as it is now and mounting ok you will see it is partitioned
so shows as 2 mounted USB drives thats the last 2 entries.

#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda11
UUID=7592a604-1321-4439-a0a3-0af4489997d0 /               reiserfs notail          0       1
# /dev/hda12
UUID=d2421d79-0624-4fa1-ac28-32eb4f856ab1 /home           reiserfs defaults        0       2
# /dev/hda1
# /dev/hda6
UUID=01600c71-2d49-4a0f-b661-7260866090d4 /media/hda6     reiserfs defaults        0       2
# /dev/hda7
UUID=4e8b32e4-d06e-458c-bc82-455ee674b021 /media/hda7     reiserfs defaults        0       2
# /dev/hda8
UUID=337b3bfe-38a7-4f46-8feb-df2e63903f18 /media/hda8     reiserfs defaults        0       2
# /dev/hda9
UUID=285fa7b8-e1fa-423c-a221-3fbf25781f5c /media/hda9     reiserfs defaults        0       2
# /dev/hdb1
# /dev/hdb5
UUID=05e91766-5e67-4dad-87de-d28e5e411186 /media/hdb5     ext3    defaults        0       2
# /dev/hda13
UUID=33f28da7-c3bd-4eea-b6f4-f04d4ebdf20c /tmp            reiserfs defaults        0       2
# /dev/hda14
UUID=cee07998-a6f0-4531-8286-64019e6ab941 /usr            reiserfs defaults        0       2
# /dev/hda10
UUID=5aeaeefa-c53a-4ca9-81b7-ad47e172b6bc none            swap    sw              0       0
# /dev/hda5
UUID=cb385003-236a-45e7-bd9c-47dec2c080c8 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

# Generated by Automatix
/dev/hda1   /media/hda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/hdb1   /media/hdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,auto,nonempty,force,locale=en_US.utf8,users    0    0
/dev/sdb5   /media/sdb5   ntfs-3g  defaults,auto,nonempty,force,locale=en_US.utf8,users    0    0
## End of Automatix mounted partitions

as you can see i used automatix but you don't have to use it if your other drives mount ok
i added after defaults." auto,nonempty,force," that makes the drive spin up so it is mounted at startup this works for me on my system.

---

### Post by casaba on 2007-07-29
Thanks all.  Automatix was the (a?) fix.  It is a bit spooky, like it read my mind:  the partitions/drives that I wanted access to are now available while the one I did not (windows partition) is not.  All good. 

For those who arrived here searching a similar problem, all I did:
Search 'Automatix' for web site, download for Feisty, install, run under Applications>System Tools, and under the Miscellaneous category, checkboxed 'Automatix read/write NTFS and FAT32 Mounter', and clicked 'Start'.  

From there it was all automatic; I was told a reboot may be necessary to properly mount the drives, but so far, no reboot and both partition and external USB hard drives are mounted and editable.

Stay tuned for round two.

---

