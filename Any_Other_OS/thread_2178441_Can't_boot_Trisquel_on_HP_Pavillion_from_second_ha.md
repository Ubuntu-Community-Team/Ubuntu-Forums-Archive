---
title: "Can't boot Trisquel on HP Pavillion from second hard drive?"
date: 2013-10-03
forum: Any Other OS
---

### Post by jadopadobhimbhadako on 2013-10-03
I created a partition of 6 gb on my second harddrive, made it ext 4, and 200mb for swap, though I don't really know what swap is for. Then I installed trisquel on it. When I start the computer, I don't get an option to boot trisquel. I couldn't find the second harddrive in the bootlist so I exchanged them and tried to boot again. Then I got a message that said "BOOT-something MISSING" and ctrl-alt-delete to restart. What's going on?

---

### Post by sandyd on 2013-10-03
moved to other os/ distro support.

---

### Post by heir4c on 2013-10-03
Boot with the live-cd/usb and when you on the desktop you open a terminal and type in:
```
fdisk -l
```
Post here the output.

---

### Post by jadopadobhimbhadako on 2013-10-03
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7f6c43d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   234438655   117115904    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bd32bd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   221852591   110926264+   7  HPFS/NTFS/exFAT
/dev/sdb2       221853696   234047055     6096680   83  Linux
/dev/sdb3       234047486   234440703      196609    5  Extended
/dev/sdb5       234047488   234440703      196608   82  Linux swap / Solaris

Disk /dev/sdc: 7820 MB, 7820083200 bytes
10 heads, 42 sectors/track, 36365 cylinders, total 15273600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    15265791     7632880    c  W95 FAT32 (LBA)

---

### Post by jadopadobhimbhadako on 2013-10-03
it's on sdb.

---

### Post by oldfred on 2013-10-03
Where did you install the boot loader for trisquel? It should be in the MBR not a partition of that drive sdb. Then in BIOS you choose to boot that drive.
What boot loader does it use?
If your error is missing bootmgr that is Windows, so you did not install the correct boot loader to the MBR.

If it uses grub2 as boot loader this may fix it.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

