---
title: "i cannot boot xp"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2007-12-16
i installed xp on other hard disk.
i dual boot them where ubuntu is installed 1st.
after i select xp from grub, the screen just display "Starting up" and nothing happens.
i still can boot xp if i change the device priority at bios.

---

### Post by diatribe on 2007-12-16
make sure your menu.lst is pointing at the correct partition for windows

---

### Post by dstew on 2007-12-16
Post to the forum the output of these two commands:```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by oliviacond on 2007-12-17
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bfa0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f644f63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris
```
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=4287ba4b-3534-405f-a0e0-1106f088a78d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Windows XP
root            (hd1,0)
makeactive
chainloader     +1

```

---

### Post by dstew on 2007-12-17
Try adding these lines to your Windows XP boot statments:```
title = Windows XP
root = (hd1,0)
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
makeactive
chainloader +1
```What seems to happen with some BIOSes and SATA drives, is that the drive enumeration changes with the boot order. Anyway, the map statements should allow Windows to boot. This is because Windows needs to believe it is on the first drive, and grub is counting Windows on the second drive. Linux, however, counts Windows on the first drive, but grub's count is what counts at boot time.

Another way to fix this is to edit your device.map file (to see it, do cat /boot/grub/device.map). But you can probably get it to work by editing the menu.lst file.

To edit the file, first make a backup, then edit using a text editor like nano:```
cp /boot/grub/menu.lst /boot/grub/menu_bak.lst
sudo nano /boot/grub/menu.lst
```After you edit the file, finish by entering control-X (also denoted ^X), enter Y to save the file, hit return. The restart and see if you can now boot Windows XP.

---

### Post by oliviacond on 2007-12-18
> **dstew said:**
> Try adding these lines to your Windows XP boot statments:```
title = Windows XP
root = (hd1,0)
[B]map (hd0) (hd1)
map (hd1) (hd0)[/B]
makeactive
chainloader +1
```What seems to happen with some BIOSes and SATA drives, is that the drive enumeration changes with the boot order. Anyway, the map statements should allow Windows to boot. This is because Windows needs to believe it is on the first drive, and grub is counting Windows on the second drive. Linux, however, counts Windows on the first drive, but grub's count is what counts at boot time.

Another way to fix this is to edit your device.map file (to see it, do cat /boot/grub/device.map). But you can probably get it to work by editing the menu.lst file.

To edit the file, first make a backup, then edit using a text editor like nano:```
cp /boot/grub/menu.lst /boot/grub/menu_bak.lst
sudo nano /boot/grub/menu.lst
```After you edit the file, finish by entering control-X (also denoted ^X), enter Y to save the file, hit return. The restart and see if you can now boot Windows XP.
it works:)

---

