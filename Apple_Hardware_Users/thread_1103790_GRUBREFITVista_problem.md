---
title: "GRUB/REFIT/Vista problem"
date: 2009-03-23
forum: Apple Hardware Users
---

### Post by tajddin on 2009-03-23
Hello all.  Last week I decided to try out Ubuntu for the first time in a while on my Intel iMac.  I already had Windows Vista installed on a third partition via refit, which worked just fine...

...until I installed the most recent release of Ubuntu.  Before installation of Ubuntu 8.1, I created a 4th partition of 10GB for testing purposes dedicated to Ubuntu.  Once Ubuntu was installed and working fine, I tried to boot into Windows Vista from the Refit menu only to receive the GRUB interface.

After selecting the default Windows Vista/Longhorn bootloader under GRUB, I receive, "Error 13."  I've tried editing  /boot/grub/menu.lst many times to correct the issue, but to no avail.

Here is my menu.lst:

[SIZE="1"]

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		640dcb30-9015-4db2-a38b-54d5767ad647
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=640dcb30-9015-4db2-a38b-54d5767ad647 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		640dcb30-9015-4db2-a38b-54d5767ad647
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=640dcb30-9015-4db2-a38b-54d5767ad647 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		640dcb30-9015-4db2-a38b-54d5767ad647
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=640dcb30-9015-4db2-a38b-54d5767ad647 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		640dcb30-9015-4db2-a38b-54d5767ad647
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=640dcb30-9015-4db2-a38b-54d5767ad647 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		640dcb30-9015-4db2-a38b-54d5767ad647
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows Vista
root           (hd0,4)
savedefault
makeactive
chainloader	+1
[/SIZE]

Here is my fdisk -l output as well if needed:

[SIZE="1"]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbff2bff2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2              26       13071   104783852   af  Unknown
/dev/sda3   *       13087       24976    95495760   af  Unknown
/dev/sda4           24992       26298    10485760   83  Linux
[/SIZE]


I also tried to boot into Super Grub, but when the CD is in the drive, GRUB just seems to hang.

I'm not certain of how to proceed.  Any help would be appreciated.

Thank you!

---

### Post by cyberdork33 on 2009-03-23
You should install GRUB to the Ubuntu partition instead of to the default MBR location (which is where the Windows bootloader is). 

Now to repair.

First, make sure to sync the partition tables with refit.

After that, boot the Vista CD and choose the recover mode. go to a terminal and use 'bootrec /fixmbr' to replace the MBR bootloader with the windows bootloader again.
More Info:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

This *should* get windows working again when you reboot, but it still may not because windows does not like when you change the partitions on the disk after it has already been installed. If windows is still not booting at this point, I don't know how to fix the problem without reinstalling.

If it does work, then you also need to reinstall grub. Follow the direction here:
[http://ubuntuforums.org/showpost.php?p=3303463&postcount=11](http://ubuntuforums.org/showpost.php?p=3303463&postcount=11)

---

### Post by tajddin on 2009-03-23
Thanks, I'll go ahead and give that a try tonight.

---

