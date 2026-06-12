---
title: "Camera Canon Powershot Pro1 doesn't mount (Ubuntu 7.10)"
date: 2007-11-04
forum: Absolute Beginner Talk
---

### Post by despotakisch on 2007-11-04
When I connect the usb camera Canon PowerShot Pro1 in Ubuntu 7.10 (Gutsy), it is recognized from gThumb as 'USB PTP Class Camera' and the model there isn't in the list of Canon Cameras.
I can import photos with the gThumb but the camera doesn't mount automatically and i can't access it with Nautilus.
Can I do this manually? How?

---

### Post by taurus on 2007-11-04
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by despotakisch on 2007-11-04
the command sudo fdisk -l gives

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2aa72aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    7  HPFS/NTFS
/dev/sda2            4866        9728    39062047+   f  W95 Ext'd (LBA)
/dev/sda5            4866        9728    39062016    b  W95 FAT32

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x88b688b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2432    19535008+  83  Linux
/dev/sdb2            2433        4865    19543072+   5  Extended
/dev/sdb5            2433        2495      506016   82  Linux swap / Solaris
/dev/sdb6            2496        4865    19036993+   b  W95 FAT32

---

### Post by taurus on 2007-11-04
What about

```
dmesg | tail
```

p.s.  Make sure your camera is plugged in.

---

### Post by despotakisch on 2007-11-04
the command dmesg | tail gives

[   49.716207] Bluetooth: L2CAP socket layer initialized
[   49.728340] Bluetooth: RFCOMM socket layer initialized
[   49.728542] Bluetooth: RFCOMM TTY layer initialized
[   49.728548] Bluetooth: RFCOMM ver 1.8
[   54.238224] NET: Registered protocol family 17
[   57.701884] NET: Registered protocol family 10
[   57.703229] lo: Disabled Privacy Extensions
[   68.323837] eth0: no IPv6 routers present
[   89.745153] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   89.909269] usb 1-2: configuration #1 chosen from 1 choice

---

### Post by Nate53085 on 2008-04-20
I am having the same problem in 8.04 with my powershot sd1100 IS

---

### Post by plasticM on 2008-05-18
> **Nate53085 said:**
> I am having the same problem in 8.04 with my powershot sd1100 IS

As am I with my Canon S5.  Very annoying.  gthumb works but I don't like it (it creates funny folders and stuff).  I just want to mount and browse my camera.

Tim

---

### Post by Chriis on 2008-05-24
IDEM here with a PowerShot S3 IS

Any help to mount it? 

Worked great in 7.10 :(:(

Chriis

---

### Post by Cod on 2008-06-08
Just adding that I have the exact same problem with my Canon Powershot A610.  FSpot sees it and is able to import photos from it.  But I wanted to use it like a USB drive and it doesn't seem to mount anywhere.

Can't remember if it used to work under 7.10.  I think I have an old 7.10 liveCD around somewhere.  I'll give it try.

---

### Post by Cod on 2008-06-08
Pfft.
Well that didn't work either.  This is very frustrating.  Anyone got any ideas?

---

