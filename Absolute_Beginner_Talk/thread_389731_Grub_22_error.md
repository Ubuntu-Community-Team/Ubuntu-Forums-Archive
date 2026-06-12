---
title: "Grub 22 error"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by recphani on 2007-03-21
My intention was to install Ubuntu on External hard drive. After going through couple of threads in the forum, I decided to disable internal hard drive in BIOS and run Ubuntu Live CD. I installed Ubuntu using Live CD on external hard drive with following steps:
1. Completely erase external hard drive.
2. Install grub on (hd0).

When I reboot the system, I activated back my internal hard drive and changed the boot sequence as 
1. Floppy Disk
2. CD
3. External Hard Drive (USB)
4. Internal Hard drive

Grub threw error message 2. Referring couple of other threads, I ran root, setup commands in Grub shell (grub>).

Here's my fdisk -l output.

```
Disk /dev/sda: 100.0 GB

Device       Boot Start   End        Blocks            ID     System
/dev/sda1               1  12161     976683201     7      HPFS/NTFS

Disk /dev/sdb: 160.0 GB

Device       Boot  Start  End        Blocks            ID     System
/dev/sdb2    *     375   19457    153284197+    5     Extended
/dev/sdb5          19084 19457      3004123+    82    Linux swap / Solaris
/dev/sdb6           375   19083     150279979+  83    Linux

Partition table entries are not in disk order

```

Here's my find /boot/grub/stage1 output

(hd0,5)

After unplugging external hard drive, I am not able to boot XP. Also, can you suggest on how and where can I download DOS bootable CD (recovery CD is not an option for me)? Do you think, for the time being, I could fix MBR using 'fdisk /mbr' and later fix grub to refer only the external hard drive while booting?

Please suggest.

---

### Post by chewearn on 2007-03-21
Windows/DOS boot disk:
[http://www.bootdisk.com/](http://www.bootdisk.com/)

Since you are planning to unplug the external drive with ubuntu, you definitely need to restore the internal drive MBR to Windows bootloader.
Then, you should re-install grub in the MBR of the external drive.

---

### Post by recphani on 2007-03-21
Thanks! I still need to fix the grub 22 error - will go through some threads & forums.

---

