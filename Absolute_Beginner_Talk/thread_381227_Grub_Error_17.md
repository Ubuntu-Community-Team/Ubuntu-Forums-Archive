---
title: "Grub Error 17"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by eyepuppy on 2007-03-10
Hey guys,

I just installed Ubuntu to my 250GB Internal HDD with the format Ext 3. I previously had Windows XP Pro installed on my 100 GB NTFS drive. When I rebooted my computer, I got a Grub Error 17. After researching the error, I found that the error 17 means that GRUB can not mount the partition. The error also states that the partition exists, but the file system can not be recognized.

After about 4 hours of searching on the forums, I finally decided to make a post. I went into the terminal and ran two commands.

sudo fdisk -l
```
Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12187    97892046    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris

Disk /dev/sdc: 37.0 GB, 37018484224 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4500    36146218+   7  HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        4500    36146218+   7  HPFS/NTFS
```

df -h
```
Filesystem            Size  Used Avail Use% Mounted on
unionfs               1.7G  658M  989M  40% /
varrun               1014M   76K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb             10M  112K  9.9M   2% /proc/bus/usb
udev                   10M  112K  9.9M   2% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M  7.6M 1007M   1% /lib/modules/2.6.17-10-generic/volatile
tmpfs                1014M   16K 1014M   1% /tmp
```

These two commands were ran through the 6.10 Install Disk (live session)

I have 4 hard drives. A Maxtor 100 GB in my SATA-3 slot formatted in NTFS, a WD 250 GB in my SATA-4 slot formatted in Ext3, and two 35 GB Raptors in my SATA-1 and SATA-2 slots formatted in NTFS (NOT in RAID). I also have a 500 GB External HDD that is currently not plugged in. My motherboard searches for the boot record in this order: SATA-3, SATA-4, SATA-1, SATA-2

From what I understand, my installation was successful, but the new Boot system (GRUB) is not working correctly.

---

### Post by dstew on 2007-03-10
It sounds like grub is trying to read its files from or write its files to one of your ntfs partitions or possibly to your swap partition. I assume you want a dual-boot system, with /dev/hda as the first disk in your BIOS boot order, and /dev/hdb1 as the partition containing the linux kernel.

What is happening is that during installation, grub stage1 was installed (probably) in the master boot record of /dev/hda, but it is either trying to write stage2 on an ntfs or swap partition, or read it from that partition at boot time.

To fix it, you will need to reinstall grub. The safest way to do this is to run the grub program from the live CD you used to install Ubuntu. Boot the live CD and start grub from the terminal.

At the grub prompt, enter

grub> find /boot/grub/stage1

This will tell you where the installer put grub's root directory. It should be on your linux partition. If so, the output should be (hd1,0). This is grub-speak for the first partition of your second disk, the way your BIOS counts them (note: not the same as your boot order, but the order in which your BIOS detects them).

To reinstall grub, make its root the same as the output of the last command:

grub>root (hd1,0)

Then install the grub booter to the MBR of the first disk:

grub>setup (hd0)

It should boot correctly after that.

---

### Post by jcostom on 2007-03-10
> **dstew said:**
> It sounds like grub is trying to read its files from or write its files to one of your ntfs partitions or possibly to your swap partition. I assume you want a dual-boot system, with /dev/hda as the first disk in your BIOS boot order, and /dev/hdb1 as the partition containing the linux kernel.


I'm in pretty much the same spot.

The system has 2 SATA drives:

SATA1 (/dev/sda) == C: for Vista
SATA2 (/dev/sdb) partitioned as:

/dev/sdb1 (ext3) 250M /boot
/dev/sdb2 (swap) 4GB
/dev/sdb3 (xfs) (the rest of the drive) /

I installed grub by doing:

root (hd1,0)
setup (hd0)

That puts the grub MBR on /dev/sda, as you suggested.  

Grub loads stage 1, and then after announcing that it's loading stage 1.5, I too get the dreaded Error 17 with no further info about the error.

Fortunately, I'm able to easily recover the Vista boot capability by booting from the vista dvd, going to repair mode, a command prompt and running:

bootrec /fixmbr
bootrec /fixboot

I've also tried installing grub by doing:

root (hd1,0)
setup (hd1)

then grab the first 512 bytes:

dd if=/dev/sdb of=edgy.mbr bs=512 count=1

Then haul the mbr file over to the Windoze side and try adding Edgy to the BCD configuration.  I get the menu option at boot time to boot Edgy, though when I select that option, I simply get, "GRUB" in the upper left corner of the screen and nothing further.

It ain't pretty, let's just say.

Anyone have further thoughts?

---

### Post by eyepuppy on 2007-03-11
Hey guys. Thanks for the comments. It seems that Linux thought Windows was not shut down right. This must have been caused due to a program that starts up before Windows to scan for file discrepancies. I booted from my Windows XP CD and ran my fixmbr and fixboot and booted back into Windows, turned off the discrepancy analysis and started the Linux install.

Installed Linux without a problem and booted into Linux. Thanks for the help!

---

