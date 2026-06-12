---
title: "Mounting SD card issue"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-05-04
Hi!
I've got a FSC Amilo Si1520 with an integrated MMC reader. When I insert my SD card nothing happens. If I insert it before I boot the computer, it usually mounts successfully, so it seems like Ubuntu supports it.
When I boot with the card inserted, it mounts as /media/disk, and the device node is /dev/mmcblk0p1, but I can't find mmcblk0p1 in /dev, so I can't mount it manually. Can anyone help me with this one?

Please note that I'm a newbie :)

---

### Post by taurus on 2007-05-04
What's the output of this command from a terminal after you insert the card into your computer?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Joakim Stokland on 2007-05-04
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1530    12288000   27  Unknown
/dev/sda2   *        1530        7905    51200000    7  HPFS/NTFS
/dev/sda3            7906       14593    53721360    5  Extended
/dev/sda5            7906        7916       88326   83  Linux
/dev/sda6            7917        8165     2000061   83  Linux
/dev/sda7            8166       11812    29294496   83  Linux
/dev/sda8           11813       14593    22338351   83  Linux

---

### Post by taurus on 2007-05-04
Well, it doesn't see it.  How about

```
dmesg | tail
```

---

### Post by Joakim Stokland on 2007-05-04
[   53.116000] Bluetooth: HCI socket layer initialized
[   53.148000] Bluetooth: L2CAP ver 2.8
[   53.148000] Bluetooth: L2CAP socket layer initialized
[   53.260000] Bluetooth: RFCOMM socket layer initialized
[   53.260000] Bluetooth: RFCOMM TTY layer initialized
[   53.260000] Bluetooth: RFCOMM ver 1.8
[   67.324000] eth0: no IPv6 routers present
[   83.748000] ipw3945: Error sending LEDS_CMD: time out after 500ms.
[   84.428000] ipw3945: Radio Frequency Kill Switch is On:
[   84.428000] Kill switch must be turned off for wireless networking to work.

---

### Post by Joakim Stokland on 2007-05-10
Anyone who knows? Thanks! :)

---

