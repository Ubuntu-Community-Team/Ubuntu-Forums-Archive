---
title: "Dual boot Ubuntu + Windows on 2 hdd's"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by SickFinga on 2007-03-01
I know, I know, this was asked many times and I checked all of the threads and I still cant make dual boot to work properly.

Here is my setup.

I got SATA drive with Windows XP on it.
IDE drive with Ubuntu.

Now here is my problem.

If I setup in BIOS to boot from SATA drive, Windows XP loads no problem, but no grub.
If I setup to boot from IDE, I get grub, Ubuntu loads fine, but when I select to boot into Windows XP, i get NTLDR missing error.

Any idea how to fix this?

Thanks.


fdisk output (hda- ubuntu drive, sda - windows) 

```

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6997    56203371   83  Linux
/dev/hda2            6998        7297     2409750    5  Extended
/dev/hda5            6998        7297     2409718+  82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       24321   195358401   42  SFS

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36482   293041633+   7  HPFS/NTFS

Disk /dev/hde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       14593   117218241    7  HPFS/NTFS

```

My menu.lst

```

title		Microsoft Windows XP Professional
rootnoverify		(hd3,0)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1

```

---

### Post by mikewhatever on 2007-03-01
Can you also post the output of 

sudo gedit /boot/grub/device.map

this is to verify, GRUB sees your HDDs as we think it does.

---

### Post by SickFinga on 2007-03-01
> **mikewhatever said:**
> Can you also post the output of 

sudo gedit /boot/grub/device.map

this is to verify, GRUB sees your HDDs as we think it does.


(hd0)	/dev/hda
(hd1)	/dev/hdb
(hd2)	/dev/hde
(hd3)	/dev/sda

---

### Post by mikewhatever on 2007-03-01
That seems to be OK, so I don't know. I'll let you know if I think of anything else :confused:

---

### Post by SickFinga on 2007-03-02
Anyone?

---

