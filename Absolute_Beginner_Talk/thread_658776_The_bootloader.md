---
title: "The bootloader"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Captain Jack on 2008-01-05
Okay, so I have three versions of Microsoft Windows (one being Vista)and Ubuntu that I would like to have on the GRUB bootloader. I know how to modifiy the menu.lst file but I cannot seem to make this work. Evertime I guess something like "hd0,1", "hd0,2" so forth...it will either say invaid partition or nothing will happen. Furthermore, I can't figure out what to write in the menu.lst file for root for my other hard drives. Any help?

---

### Post by overdrank on 2008-01-05
> **Captain Jack said:**
> Okay, so I have three versions of Microsoft Windows (one being Vista)and Ubuntu that I would like to have on the GRUB bootloader. I know how to modifiy the menu.lst file but I cannot seem to make this work. Evertime I guess something like "hd0,1", "hd0,2" so forth...it will either say invaid partition or nothing will happen. Furthermore, I can't figure out what to write in the menu.lst file for root for my other hard drives. Any help?

HI and I believe this link will help
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)
Good luck!

---

### Post by Captain Jack on 2008-01-07
Thank you for that link, it was very insightful. My qestion is how do I find out what the root is for each of my hard drive partitions? Now, I have one SATA drive and one USB external hard drive on my computer. I tried using the command fdisk -l and all that is displayed is information about my external hard drive. Any help please?

---

### Post by overdrank on 2008-01-07
> **Captain Jack said:**
> Thank you for that link, it was very insightful. My qestion is how do I find out what the root is for each of my hard drive partitions? Now, I have one SATA drive and one USB external hard drive on my computer. I tried using the command fdisk -l and all that is displayed is information about my external hard drive. Any help please?

HI and do you have a mix of IDE and SATA drives? I have seen where this is a issue but this thread may help
[http://ubuntuforums.org/showthread.php?t=654628&highlight=drive](http://ubuntuforums.org/showthread.php?t=654628&highlight=drive)

---

### Post by erginemr on 2008-01-07
> **Captain Jack said:**
> Thank you for that link, it was very insightful. My qestion is how do I find out what the root is for each of my hard drive partitions? Now, I have one SATA drive and one USB external hard drive on my computer. I tried using the command fdisk -l and all that is displayed is information about my external hard drive. Any help please?

Hello,

You should try "sudo fdisk -l", to see if it helps. Also the commnad "blkid" may give you some more information on your hard drives.

---

### Post by Captain Jack on 2008-01-08
Okay, sudo -l worked and this is what was displayed:

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006af8a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       91200   630165690    f  W95 Ext'd (LBA)
/dev/sda5           12749       25496   102398278+   7  HPFS/NTFS
/dev/sda6           38245       50992   102398278+   7  HPFS/NTFS
/dev/sda7           50993       62465    92156841   83  Linux
/dev/sda8           62466       63740    10241406   83  Linux
/dev/sda9           63741       64250     4096543+  82  Linux swap / Solaris
/dev/sda10          64251       91200   216475843+   7  HPFS/NTFS

Now, I just want to be able to boot into sda1, sda5, and sda6. Below is my menu.lst:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a32e753d-9082-4881-b3e3-b08432b60090 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a32e753d-9082-4881-b3e3-b08432b60090 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Professional x64
root		(hd0,0)
savedefault
makeactive
chainloader	+1

I am a little stuck on if I should try move or hide and how I should do it. Any help please?

---

### Post by erginemr on 2008-01-08
Well, sda1 is (hd0,0), sda5 is (hd0,4) and sda6 is (hd0,5). But beyond that point is also beyond my comprehension.

The following HOWTO implies that it is impossible to boot several Windows versions directly from Linux and you have to rely on Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)

However, the following three sections of this excellent guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_OS_entries)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_more_on_the_same_disk)

states that it is possible and looks very promising. I believe your case corresponds to the 3rd link.

As I only have windows xp as dual-booted to ubuntu, I cannot check it myself. But if you are determined to venture, I would suggest you to first back up your "/boot/grub/menu.lst" file.

---

