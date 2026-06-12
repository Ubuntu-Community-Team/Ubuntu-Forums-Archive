---
title: "No CD/DVD writer found"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by dcas1 on 2007-08-27
On Kubuntu 7.04 I had apt install several upgrades then lost access to dvd, Now K3b opens with this message: No CD/DVD writer found. The dvd worked OK before the upgrades and I replaced it with another - same result.. 
Here's the result of 
dmesg |grep hd

[   17.359385]     ide0: BM-DMA at 0xcc00-0xcc07, BIOS settings: hda:pio, hdb:pio
[   17.359396]     ide1: BM-DMA at 0xcc08-0xcc0f, BIOS settings: hdc:pio, hdd:pio
[   17.774768] hda: MAXTOR STM3200820A, ATA DISK drive
[   19.543930] hda: max request size: 512KiB
[   19.583071] hda: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(100)
[   19.607439] hda: cache flushes supported
[   19.607480]  hda: hda1 hda2 < hda5 >
[   31.333429] EXT3 FS on hda1, internal journal
The DVD is on IDE2 so I suppose it should be hdc or hdd but it doesn't show up in dmesg. How can I gain access to this DVD drive? thanks

---

### Post by aspen_dv on 2007-08-28
Try:
mount 
The look for anything links to your dvd drive. Or you can also look for it in
more /etc/fstab

Then try to remount the drive again
Something like
mount -t iso9660 /dev/hdc /media/cdrom
(assuming that /media/cdrom is the correct directory, and /dev/hdc is correct device)

---

