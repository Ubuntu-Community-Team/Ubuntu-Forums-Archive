---
title: "Grub: Error 17. Should i reinstall ubuntu?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by john.n on 2007-01-17
Hi, 
been using Ubuntu for few days now, not to sure what happened but now when i start my laptop i get Grub error message, error 17. Looked through the other posts but i dont have an XP boot disc, i was wondering, would removing the Ubuntu partitions then reinstalling Ubuntu work? I have the liveCD, so if there is anyway of fixing GRUB with it, any help would be great, other posts(and google) havnt led to anything clear.

Thanks

---

### Post by mikewhatever on 2007-01-17
Try reinstalling GRUB with LiveCD.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by CroEragon on 2007-01-17
Download and burn SuperGRUB. Use it as live cd and try to repair GRUG with it. If you can't use it to bott in your hard disc installation and post output of this:
```
cat /boot/grub/menu.lst
```
EDIT: or you can use upper sugesstion to reinstall.

---

### Post by anaconda on 2007-01-17
error 17 means that grub didn't find linux kernel from where it searched it.

So you can either boot with liveCD and check that the path is correct in your /boot/grub/menu.lst file, and if not then repair it..

On the other hand.. If you reinstall ubuntu it will also reinstall grub, and it should start working again.

---

### Post by john.n on 2007-01-17
How do i access /boot/grub/menu.ls while using the live cd, its only bringing up the files that are in the os on the LiveCD?

---

### Post by Sef on 2007-01-17
> error 17 means that grub didn't find linux kernel from where it searched it.


That is incorrect.  This is [GRUB]("http://www.linuxselfhelp.com/gnu/grub/html_chapter/grub_13.html") error 17:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

From the Ubuntu Live CD, open the Terminal (Applications > Accessories > Terminal),

then type in this command:

```
sudo fdisk -l
```

then paste your partition list here.

---

### Post by john.n on 2007-01-17
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7946    63826213+   7  HPFS/NTFS
/dev/hda2            7947       11133    25599577+  83  Linux
/dev/hda3           11134       11388     2048287+  82  Linux swap / Solaris
/dev/hda4   *       11390       12161     6201090    c  W95 FAT32 (LBA)


Is there anyway to write a disc using the LiveCD? (Would imagine not, just dont have access to another computer to write GRUB LiveCD)

---

### Post by Sef on 2007-01-17
> Device Boot Start End Blocks Id System
/dev/hda1 1 7946 63826213+ 7 HPFS/NTFS
/dev/hda2 7947 11133 25599577+ 83 Linux
/dev/hda3 11134 11388 2048287+ 82 Linux swap / Solaris
/dev/hda4 * 11390 12161 6201090 c W95 FAT32 (LBA)

I would try changing the boot from /dev/hda4 to hda1, if that is XP.  If it isn't, please tell me.

---

### Post by john.n on 2007-01-17
How do i do that? Using gparted? that just gives me option to reformat it if i want to rename it.

---

