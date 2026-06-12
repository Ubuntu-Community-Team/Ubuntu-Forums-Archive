---
title: "Big Boot Problems (GRUB ERROR 21)"
date: 2007-02-04
forum: Absolute Beginner Talk
---

### Post by tother on 2007-02-04
Hey,
first, i come from Germany, but the German board couldn't help me...
And sorry for my bad English :) 

My system:
Intel C2D E6300
MSI P965 Neo-f
Samsung SP2504
LG GSA H10N (DVD burner)
installed OS: MS Windows XP Home

I want to install Ubuntu parallel to Windows. So I installed Ubuntu without any problems.
But if boot there allways appears Grub Stage 1.5  and ERROR 21 (he cannot find any hdds???)
Plz help me!

---

### Post by tother on 2007-02-04
has no-one any ideas?

---

### Post by cptjaben on 2007-02-04
so you installed Windows and then Ubuntu afterward? you could always try reinstalling grub by using the Ubuntu Live CD. Hope this helps.

---

### Post by confused57 on 2007-02-04
> **tother said:**
> Hey,
first, i come from Germany, but the German board couldn't help me...
And sorry for my bad English :) 

My system:
Intel C2D E6300
MSI P965 Neo-f
Samsung SP2504
LG GSA H10N (DVD burner)
installed OS: MS Windows XP Home

I want to install Ubuntu parallel to Windows. So I installed Ubuntu without any problems.
But if boot there allways appears Grub Stage 1.5  and ERROR 21 (he cannot find any hdds???)
Plz help me!

Here's a description of grub error 21:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

You can boot up the live cd, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".
This will show your partition table(s).

If you have 2 or more hard drives, make sure the hd jumper settings are correct and the hard drives are recognized & setup properly in bios.

---

### Post by tother on 2007-02-06
sry for my late answer

1st I tried to reinstall GRUB by using a UBUNTU Live CD but and it didn`t help
so now I installed UBUNTU on a 2nd HDD but I disconnected the 1st HDD for looking if it runs on my computer. And it ran. But I want to have both OSs on my computer.
So I reconnected the 1st HDD and reinstalled UBUNTU ...
Again the ERROR 21. I have installed GRUB on hd0 and on sda (the Windows partition) but it didn`t help.
Ah both HDDs are S-ATA HDDs... 

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30401   192996877+   f  W95 Ext'd (LBA)
/dev/sda5           12749       19122    51199123+   7  HPFS/NTFS
/dev/sda6           19123       25496    51199123+   7  HPFS/NTFS
/dev/sda7           25497       30400    39391348+   7  HPFS/NTFS
/dev/sda8           30401       30401        8001   83  Linux
/dev/sda9            6375       12748    51199092    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23947   192354246   83  Linux
/dev/sdb2           23948       24321     3004155    5  Extended
/dev/sdb5           23948       24321     3004123+  82  Linux swap / Solaris
```

On sdb the Linux partition has about 183 GB.
On sda the small Linux partion is an old waste ...

---

### Post by confused57 on 2007-02-06
I assume your bios detects your sdb OK, since you were able to install Ubuntu to this drive and boot up without any problems.

Here's how I have my system set up(with IDE drives), but it should work ok with SATA:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

If you can, try setting the Ubuntu drive as the first hard drive boot device(leave it connected as sdb for now), then in the grub menu at bootup(if you have grub also installed to hd1), select your Ubuntu entry, press "e" to edit, then change the root from (hd1,0) to root (hd0,0), then press "b" to boot.  This change is only temporary, but see what happens, it won't affect your Ubuntu installation.

Grub can always be reinstalled using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

See edit above=leave Ubuntu drive connected as sdb...

---

### Post by marx2k on 2007-02-06
You also want to check the grun menu in /boot/grub/menu.lst

make sure your 'root' settings are correct for the hard drives.

This can also be attempted during boot at the grub MENU (type e when youre at the menu... you may have to unhide the menu to hit E by hitting escape) (This is from memory, so if Im wrong, dont smack me) :)

---

