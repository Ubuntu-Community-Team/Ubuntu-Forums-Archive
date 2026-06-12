---
title: "problem with boot record on drive"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by JulioB on 2006-11-18
Hello. I've tried searching on this topic but haven't quite found the solution to the problem I'm experiencing.

I recently installed Edgy Eft and ran into a few issues. First I couldn't boot Linux, and now I can't boot Windows.

The initial installation was smooth enough, and I specified GRUB to install to the master boot table, alongside my existing Windows XP Pro (ok, maybe not the smartest move, but there we have it..). After booting up Windows again I could no longer get into Ubuntu (I was forbidden permission to access the drive). The drive in question is SATA and has four partitions, arranged as follows: 1 (or 0)=windows NTFS, 2=edgy EXT3, 3=swap, 4=Win data (NTFS).

I followed an online tutorial from linuxdevcenter [http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html) regarding setting up the dual booting, and tried following that as closely as possible. I kept getting boot problems, either error 17 or 22, at various stages.

Then I reinstalled Edgy, this time specifying LILO for the boot and the Ubuntu partition as the destination, so I could put the links together later without making too much of a mess. This mucked up the boot record more than I could ever believe: I loaded up my Windows CD, tried fixmbr and fixboot (one after another), and attempted reinstalling (as I thought Windows would be keen to nuke any sign that Linux had ever been there), but after running through the motions, it rebooted and promptly loaded up Edgy via LILO again ](*,) .

Can anyone think of a way I can get LILO to loosen its grip on this drive? I have other drives too

Thanks in advance,

Julio

---

### Post by Sef on 2006-11-19
That's an old tutorial.   I have dual booted with GRUB and had no problems.  Instead of installing LILO, install [GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

Note: You have have change something like permissions, so they may need to be reset.

---

### Post by confused57 on 2006-11-19
You can install grub using the desktop live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Here's a great site for grub, bootloaders, mbr, etc:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by JulioB on 2006-11-19
Thanks for your helpful replies, Sef and confused57.

I'll try these things out and see where it takes me :).

---

### Post by JulioB on 2006-11-22
Hello again :D.

... I've been experimenting and reading many various helpful tutorials, manuals and guides, and I think I discovered why Lilo was being so cantankerous (I had the second=Ubuntu partition set as bootable..)

I still can't get dual-booting working on my system though. I completely wiped my drive, then I followed the installation, but once Windows XP has started up for the first time (via the new Grub page), my bootloader is gone. Is this anything to do with the fact that the drive is SATA? If not, what would be the contributing factor? Is there anything in particular I need to bear in mind regarding this?

In BIOS this drive is set as HD primary boot. My (new) partitions are, with approximate sizes (numbered by physical position on drive):

1 Windows XP Pro 20GB: NTFS *flagged as bootable
2 Ubuntu 64bit Edgy 20GB: EXT3
3 Swap 2GB: SWAP
4 Shared/Spare/Unused 20GB: FAT32: reserved for recovery/imaging purposes
5 /Home 137GB: EXT3 (data storage)

I installed Windows first, everything went fine. Then Ubuntu, setting Grub to the MBR (0,0) which boots Ubuntu by default (0,1)* with the option of Windows (0,0) down the bottom.

* What was strange, is that Grub had (3,1) as the default reference (non-existent partition), and I had to do an on-the-fly e-edit/b-boot thing to get into Ubuntu before editing /boot/grub/menu.lst so that it actually worked.

The Windows portion of menu.lst looks like this (may need tweaking?):

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


No matter how I attempt this dual-booting thing, the first time I run Windows XP (via Grub) after installing Ubuntu it overwrites Grub with the plain Windows loader.

Any advice on what to try next?

Julio :)

---

### Post by confused57 on 2006-11-22
If you can boot to Ubuntu(or use the desktop live cd), open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L".

Post the results of the above commands, and give us a little information about what's on each of your hard drives & if you have all SATA, or a mix of IDE & SATA.

You might also want to post the output of:
```
cat /boot/grub/device.map
```

Your mbr is actually on hd0 or sda...(hd0,0) is  the partition Windows is located on, not the mbr...you definitely do not want to install grub to (hd0,0).

You can (re)install grub with the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by JulioB on 2006-11-22
Thanks so much for your reply.

Here's the output... (the drives are a mixture, in more ways than one :p)
NOTE: I tried removing the bootable flags for the other drives (sdc1 and hdd1) in fdisk, but it didn't happen, even on reboot.

sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4982    19535040   83  Linux
/dev/sdb3            4983        7414    19535040    b  W95 FAT32
/dev/sdb4            7415       24321   135805477+   5  Extended
/dev/sdb5            7654       24321   133885710   83  Linux
/dev/sdb6            7415        7652     1911672   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       14593   117218241    7  HPFS/NTFS

and the other one..

cat /boot/grub/device.map
(hd0)   /dev/hdc
(hd1)   /dev/hdd
(hd2)   /dev/sda
(hd3)   /dev/sdb
(hd4)   /dev/sdc


Hehe after looking at this latest output I'm even more confused than ever :D. Where do I go from here?

Thanks,

Julio

---

### Post by kimro on 2006-11-22
I've had a similar mbr problem with my test laptop in the past after I decided to uninstall Fedora and reinstall Windows XP completely.

System would install Windows XP fine but would never reboot due to missing mbr. I couldn't get any of mbr tools both on Windows or Fedora cds to fix the problem. Finally, I tried out the hdd nuke utility on Ultimate Boot CD ([http://www.ultimatebootcd.com/)](http://www.ultimatebootcd.com/)), which fixed my messed up mbr.

Hope this helps.

---

### Post by JulioB on 2006-11-22
Thanks kimro, I'll definitely look into that :).

---

