---
title: "External Hard Drive Not Showing Up"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by bt224 on 2007-12-28
I got a new HD for my laptop. I took the old one out that had Gutsy installed and put into an enclosure. The drive will mount on my desktop (also running Gutsy), but will not show up on the laptop. I don't mean won't mount, it doesn't show up at all. I Gparted the drive on using the desktop to Ext3, so it's clean. I used remastersys to make a custom image to install on the new HD, but not sure if that matters. What could be the problem?

---

### Post by taurus on 2007-12-28
Can you post the output of this command from a terminal?  Make sure it is plugged in and power on.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by bt224 on 2007-12-28
Here it is:


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000142f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris



When plugged into the other computer, it shows up as SDC1

---

### Post by taurus on 2007-12-28
What about

```
dmesg | tail
```

---

### Post by bt224 on 2007-12-28
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000142f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
bt224@bt224-laptop:~$ dmesg | tail
[11104.340000] hub 4-6:1.0: over-current change on port 2
[11104.852000] hub 4-6:1.0: over-current change on port 2
[11105.364000] hub 4-6:1.0: over-current change on port 2
[11106.132000] hub 4-6:1.0: over-current change on port 2
[11106.900000] hub 4-6:1.0: over-current change on port 2
[11107.412000] hub 4-6:1.0: over-current change on port 2
[11107.924000] hub 4-6:1.0: over-current change on port 2
[11108.436000] hub 4-6:1.0: over-current change on port 2
[11108.948000] hub 4-6:1.0: over-current change on port 2
[11109.460000] hub 4-6:1.0: over-current change on port 2

---

### Post by bt224 on 2007-12-28
I have no idea what that all means.

---

### Post by piousp on 2008-02-05
I have a similar problem

My HD was working on my laptop, until i updated the 'linux headers' with the gnome updater.
Now, is just not showing up. I tried to use the 'mount' command, but i just dont know how to use, even after reading the manual.


sudo fdisk -l
```

piousp@SPQR:~$ sudo fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pistas, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0x58000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1               1           7       56196   de  Utilidad Dell
/dev/sda2   *           8        3947    31648050    7  HPFS/NTFS
/dev/sda3            3948        9487    44500050   83  Linux
/dev/sda4            9488        9729     1943865    5  Extendida
/dev/sda5            9488        9729     1943833+  82  Linux swap / Solaris

```

Now dmesg | tail
```

piousp@SPQR:~$ dmesg | tail
[ 2529.700000] usb 2-1: new full speed USB device using uhci_hcd and address 6
[ 2529.824000] usb 2-1: device descriptor read/64, error -71
[ 2530.048000] usb 2-1: device descriptor read/64, error -71
[ 2530.264000] usb 2-1: new full speed USB device using uhci_hcd and address 7
[ 2530.384000] usb 2-1: device descriptor read/64, error -71
[ 2530.612000] usb 2-1: device descriptor read/64, error -71
[ 2530.828000] usb 2-1: new full speed USB device using uhci_hcd and address 8
[ 2531.240000] usb 2-1: device not accepting address 8, error -71
[ 2531.352000] usb 2-1: new full speed USB device using uhci_hcd and address 9
[ 2531.760000] usb 2-1: device not accepting address 9, error -71

```

lsusb

```

piousp@SPQR:~$ lsusb
Bus 004 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

```

Can anyone help?

---

