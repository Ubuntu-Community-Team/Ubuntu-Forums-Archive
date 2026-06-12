---
title: "What happened to my windows partition?"
date: 2006-03-17
forum: Absolute Beginner Talk
---

### Post by varun on 2006-03-17
The following is the output of sudo fdisk-l on my PC
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
240 heads, 63 sectors/track, 5169 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         605     4573768+   b  W95 FAT32
/dev/hda2   *         606        5168    34496280    7  HPFS/NTFS

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1305    10482381   83  Linux
/dev/hdd2            1306        7832    52428127+   7  HPFS/NTFS
/dev/hdd3            7833       14359    52428127+   7  HPFS/NTFS
/dev/hdd4           14360       19457    40949685    7  HPFS/NTFS

```

I had windows installed on /dev/hda2. I was having trouble with GRUB as I had reinstalled ubuntu on the 160GB HDD and removed the HDD on which it was previously installed. In order to reinstall the GRUB i executed the following command after booting from the install CD and entering recover.

```
grub-install /dev/hda2
```
After this I was not even able to mount the partition and got and error.
```
varun@varun:~$ sudo mount /dev/hda2 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Earlier this was working fine. Do I have to format this partition and is there any way I can recover the data of this partition? I am new to linux and any help would be greately appreciated.

---

### Post by Haegin on 2006-03-17
Use the live CD to get into ubuntu and mount the windows partition somewhere in your home directory. Then you should be able to access all your windows files and back everything up to cds or whatever. NTFS partitions are read-only so you wont be able to change any thing.

Just learn from this and always err on the side of caution in future. I have suffered and you do learn pretty fast...

---

