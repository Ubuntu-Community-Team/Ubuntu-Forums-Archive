---
title: "No Partitions on hda"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by tonyr1988 on 2007-01-09
I've got Ubuntu installed on my second hard drive (hdb) and hda is partitioned like this:

20GB - NTFS - WinXP
140GB - ext2 - Shared

But, looking into /dev, I only see hda - there isn't an hda1 or hda2.

I installed GParted, and it shows both of them there, but they have warning icons.

For hda1, it complains about it being ntfs - no surprise.
For hda2, it's saying:

> dumpe2fs 1.39 (29-May-2006)
dumpe2fs: No such file or directory 
while trying to open /dev/hda2

Also, when first installing Ubuntu, it didn't add WinXP into my GRUB menu, so something's not right. For GRUB, I just manually added it and it works just fine, but I don't know what to do about this.

P.S. Here's the output from fdisk -l:

> Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2782    22346383+   7  HPFS/NTFS
/dev/hda2            2783       19929   137733277+  83  Linux

Disk /dev/hdb: 15.3 GB, 15393079296 bytes
255 heads, 63 sectors/track, 1871 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1791    14386176   83  Linux
/dev/hdb2            1792        1871      642600    5  Extended
/dev/hdb5            1792        1871      642568+  82  Linux swap / Solaris

---

### Post by sardion on 2007-01-09
Is there any data on /dev/hda2 ?

If not, I suggest refomatting it (using GParted or using the command "mke2fs" in terminal).

If there is data, look in /var/log/messages for  anything related.

---

### Post by tonyr1988 on 2007-01-09
Nope, not data on it, so I wouldn't mind wiping it, but neither GParted nor mke2fs will work - they're saying /dev/hda2 doesn't exist.

Output from "more /var/log/messages | grep hda":
> Jan  9 16:14:35 ubuntu-desktop kernel: [   25.578355]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
Jan  9 16:14:35 ubuntu-desktop kernel: [   25.867718] hda: Maxtor 6L160P0, ATA DISK drive
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.847155] hda: max request size: 512KiB
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.867001] hda: 320173056 sectors (163928 MB) w/8192KiB Cache, CHS=19929/255/63, UDMA(133)
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.868629] hda: cache flushes supported
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.868682]  hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.875955] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.876615] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.876621] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.884257] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.884263] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.884589] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.884595] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.942403] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.942409] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.943403] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.943408] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.950701] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.950707] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.951377] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   27.951383] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.008855] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.008861] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.008870] end_request: I/O error, dev hda, sector 0
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.009207] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.009213] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.010205] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.010211] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.017162] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.017167] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.018176] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 16:14:35 ubuntu-desktop kernel: [   28.018182] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   25.971277]     ide0: BM-DMA at 0xfb00-0xfb07, BIOS settings: hda:DMA, hdb:DMA
Jan  9 17:06:51 ubuntu-desktop kernel: [   26.260621] hda: Maxtor 6L160P0, ATA DISK drive
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.244108] hda: max request size: 512KiB
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.263868] hda: 320173056 sectors (163928 MB) w/8192KiB Cache, CHS=19929/255/63, UDMA(133)
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.265466] hda: cache flushes supported
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.265518]  hda:hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.285758] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.286835] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.286841] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.294056] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.294062] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.294809] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.294814] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.352206] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.352213] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.352648] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.352655] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.360511] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.360517] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.361596] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.361603] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.418675] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.418681] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.418690] end_request: I/O error, dev hda, sector 0
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.419426] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.419432] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.420421] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.420426] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.426974] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.426980] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.427420] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Jan  9 17:06:51 ubuntu-desktop kernel: [   28.427425] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }

---

### Post by tonyr1988 on 2007-01-10
I added ide=nodma to the "kernel" line of /boot/grub/menu.lst, rebooted, and it works perfectly.

---

