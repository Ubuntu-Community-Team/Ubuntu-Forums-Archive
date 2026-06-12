---
title: "Unable to mount volume (NTFS Problem)"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by 2_of_8 on 2006-07-20
I cannot access my partitions (which are in NTFS format). There are different error messages, however:

Unable to mount the selected volume.
error: device /dev/hda1 is not removable

error: could not execute pmount

and

The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "disks-conf-hdb2".

(these are for 2 different drives)


This is actually the one thing that's preventing me from loving Linux. If anyone could help me, I'll stay on this OS for sure. However, if I can't access those files, I just might have to go back to ... <shudder>

Thank you very much in advance.

---

### Post by aysiu on 2006-07-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by 2_of_8 on 2006-07-21
This is what
**sudo nano /etc/fstab**
puts out:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I don't see my NTFS partition anywhere in there.

This is the result of
**sudo fdisk -l**

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2014    16177423+  83  Linux
/dev/hda2            2080        9105    56436345    f  W95 Ext'd (LBA)
/dev/hda3            2015        2079      522112+  82  Linux swap / Solaris
/dev/hda4   *        9106        9729     5012280   83  Linux
/dev/hda5            2080        9073    56179273+  82  Linux swap / Solaris
/dev/hda6            9074        9105      257008+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10199    81923436    7  HPFS/NTFS
/dev/hdb2           10200       16709    52291575    7  HPFS/NTFS
```

I'm supposed to change the fstab document, according to the manual. But the partition isn't there :|

---

### Post by aysiu on 2006-07-21
Well, basically, the bottom line is that it has to be in there.

Either it's already in there (which is not the case here) incorrectly and you have to correct it...

... or (as is the case here), it's not there and you have to add it. So, assuming you've already done ```
sudo mkdir /windows1
sudo mkdir /windows2
``` you should add these two lines to your /etc/fstab file: ```
/dev/hdb1 /windows1 ntfs nls=utf8,umask=0222 0 0
/dev/hdb2 /windows2 ntfs nls=utf8,umask=0222 0 0
```

---

### Post by 2_of_8 on 2006-07-22
I can't save the /etc/fstab file, it says it's read-only.

---

### Post by aysiu on 2006-07-22
```
sudo nano -B /etc/apt/sources.list
``` To save: Control-X, Y, Enter.

---

### Post by 2_of_8 on 2006-07-22
Control-X does nothing. Am I opening the file wrong? I opened it from Places->Computer.

And what is the command you just pasted for?

---

### Post by benduenga on 2006-07-22
I boot linux from an external hd and usb port, which allows my fiancee to use windows.  I was able to configure the mounth on my NFTS today.  If you follow Aysiu's advice it should work.  Keep up the good work.  If you search NFTS Mount on the forums there are many helpful threads and links.

---

### Post by aysiu on 2006-07-22
> **2_of_8 said:**
> Control-X does nothing. Am I opening the file wrong? I opened it from Places->Computer.

And what is the command you just pasted for?
The command gets pasted into the terminal--that's how you edit the /etc/fstab file... from the terminal.

If you wish to edit it graphically, press Alt-F2 and type ```
gksudo nautilus
``` This will open a browser window with root privileges.

---

### Post by 2_of_8 on 2006-07-22
fstab has been edited to```
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1	/windows1	ntfs	nls=utf8,umask=0222	0	0
/dev/hdb2	/windows2	ntfs	nls=utf8,umask=0222	0	0
```
and this is
sudo fdisk -l```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2014    16177423+  83  Linux
/dev/hda2            2080        9105    56436345    f  W95 Ext'd (LBA)
/dev/hda3            2015        2079      522112+  82  Linux swap / Solaris
/dev/hda4   *        9106        9729     5012280   83  Linux
/dev/hda5            2080        9073    56179273+  82  Linux swap / Solaris
/dev/hda6            9074        9105      257008+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       10199    81923436    7  HPFS/NTFS
/dev/hdb2           10200       16709    52291575    7  HPFS/NTFS
```
The hardrive hdb does not show up in Computer. hda, however does - but is still inaccessible.```
Unable to mount the selected volume.
error: device /dev/hda1 is not removable

error: could not execute pmount
``````
Unable to mount the selected volume.
error: device /dev/hda5 is not removable

error: could not execute pmount
```

---

### Post by aysiu on 2006-07-22
Paste this command in ```
sudo mount -a
``` Then go to Places > Computer > Filesystem > windows1

---

### Post by 2_of_8 on 2006-07-23
... whoa.

I am shocked :p. I didn't expect it to work out, but it did!

Thank you very much.

---

