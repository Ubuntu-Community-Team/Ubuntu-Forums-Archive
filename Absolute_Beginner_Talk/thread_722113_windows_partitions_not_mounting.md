---
title: "windows partitions not mounting"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by drunkmatador on 2008-03-12
My windows partitions suddenly are not showing up in Ubuntu anymore. I changed my /etc/fstab back to what it originally was and they're still not showing up. When i run fdisk -l i get a long list of weird devices that weren't there before. What's all this about?

"Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x78637863

Device Boot Start End Blocks Id System
/dev/hda1 * 1 9728 78140128+ 7 HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4abc4be1

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 4784 38427448+ 83 Linux
/dev/hdb2 4785 4865 650632+ 5 Extended
/dev/hdb5 4785 4865 650601 82 Linux swap / Solaris

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x806e103c

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 19929 160079661 7 HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95245040

Device Boot Start End Blocks Id System
/dev/sda1 * 1 19457 156288321 7 HPFS/NTFS

Disk /dev/dm-0: 80.0 GB, 80015491584 bytes
255 heads, 63 sectors/track, 9727 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/dm-0p1 ? 13578 119522 850995205 72 Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-0p2 ? 45382 79243 271987362 74 Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-0p3 ? 10499 10499 0 65 Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-0p4 167628 167631 25817+ 0 Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-1: 163.9 GB, 163921572864 bytes
255 heads, 63 sectors/track, 19928 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/dm-1p1 ? 13578 119522 850995205 72 Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2 ? 45382 79243 271987362 74 Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3 ? 10499 10499 0 65 Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4 167628 167631 25817+ 0 Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/dm-2: 160.0 GB, 160039240704 bytes
255 heads, 63 sectors/track, 19456 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

Device Boot Start End Blocks Id System
/dev/dm-2p1 ? 13578 119522 850995205 72 Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-2p2 ? 45382 79243 271987362 74 Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-2p3 ? 10499 10499 0 65 Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-2p4 167628 167631 25817+ 0 Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order"

---

### Post by jan quark on 2008-03-12
really suddenly? out of the blue?
hmmm
have you altered you fstab file?

---

### Post by drunkmatador on 2008-03-12
yes, the other day i was altering it trying to get another drive to work. but like i said in my first post, i reverted back to the original fstab after this error started, so shouldn't it have gone away?

it's really irritating, i still can't get either of the drives to work. 

do you think i could have damaged them? the only time i used them was for playing snes roms on emulators i downloaded. i did save state a few times, could that have wrote to the NTFS or FAT and ruined something.

please any help would be appreciated.

---

