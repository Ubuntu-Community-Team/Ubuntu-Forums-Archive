---
title: "SD card crashed/failed?"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by GlennW on 2008-03-29
I have a 2 GB SD card (cheap generic brand) that I've been using in my Pentax Optio50 for about six months with great satisfaction. Yesterday it said "Memory card error." I had initially purchased two cards and swapped them. Joy again.

Question: Is there a way to reformat/revitalize the SD card or is it "pooched"?

Thanks

---

### Post by mcduck on 2008-03-29
As long as the card is not physically damaged but only suffers from corrupted file system or partition table it's quite easy to get it working again:

First turn off automatic mounting of removable drives (in System/Preferences/Removable Drives and Media), then plug the card in to your reader, and use fdisk or gparted to remove the existing partition from the card and make a new FAT16 or FAT32 partition.

If you are unsure about what device name the card uses, or if you want to check if it's even detected at all, open a terminal and run "tail -f /var/log/dmesg" before plugging the card in. You should see how the system detects the card and what device name it gets from the output. (you can press ctrl-c to stop printing the log file)

---

### Post by GlennW on 2008-03-29
Thanks mcduck for your response. Here's the output from tail -f /var/log/dmesg:

[INDENT][   43.384451] parport_pc 00:09: reported by Plug and Play ACPI
[   43.384567] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   43.426644] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08c9)
[   43.466053] usbcore: registered new interface driver uvcvideo
[   43.466064] USB Video Class driver (v0.1.0)
[   43.910662] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[   43.910673] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   45.744016] lp0: using parport0 (interrupt-driven).
[   45.831753] Adding 658624k swap on /dev/sda5.  Priority:-1 extents:1 across:658624k
[   46.248354] EXT3 FS on sda3, internal journal
[/INDENT]

Also, here is the output from fdisk -l

[INDENT]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2cdf2cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496    7  HPFS/NTFS
/dev/sda3            3672        9647    48002220   83  Linux
/dev/sda4            9648        9729      658665    f  W95 Ext'd (LBA)
/dev/sda5            9648        9729      658633+  82  Linux swap / Solaris

Disk /dev/sdb: 2045 MB, 2045247488 bytes
47 heads, 46 sectors/track, 1847 cylinders
Units = cylinders of 2162 * 512 = 1106944 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1848     1997188+   6  FAT16

Disk /dev/sdc: 1014 MB, 1014497280 bytes
65 heads, 32 sectors/track, 952 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         953      990704    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 64, 32) logical=(952, 39, 32)
[/INDENT]

The SD card is 2 GB and there's a USB stick that 1 GB.

I apologize I'm quite the newb so virtually all of this makes no sense to me. Your input and advice is greatly appreciated.

---

### Post by mikeyphi on 2008-03-29
Your 2Gb SD card is 'sdb'
the 1Gb stick is 'sdc'

---

### Post by mcduck on 2008-03-30
Ok. Now just install gparted from the repositories, as you'll probably want to use a graphical tool. Then  use that to access /dev/sdb, delete the existing partition and create a new one & format it to FAT16 (gparted might actually have VFAT instead of FAT16). I really can't give any more specific help about using gparted, as I don't gave my LInux machine around at the moment. But the program is quite easy and you should be able to figure it out quite easily.

---

