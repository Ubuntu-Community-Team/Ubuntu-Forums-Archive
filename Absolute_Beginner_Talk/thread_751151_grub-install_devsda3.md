---
title: "grub-install /dev/sda3"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by toontastic on 2008-04-10
Ok I messed up :) I typed in grub-install /dev/sda3 and now when I boot my machine up I no longer get the options to boot Windows or Edubuntu It just automatically boots me into Ubuntu. I've read the instructions [http://www.josephhall.org/grub_install_hda1.html](http://www.josephhall.org/grub_install_hda1.html) but they seem to suggest that I should have a Windows disk which I don't (no CD drive on laptop therefore no Windows CD) surely there is a way in Ubuntu to fix this problem ? 

Thanks in advance.

---

### Post by bumanie on 2008-04-10
Could you post the output of fdisk -l  (that is a lower case L)

---

### Post by toontastic on 2008-04-10
It's almost back to normal after restoring my backup of menu.lst but it's missing Edubuntu

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8abeab9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4329    34772661    7  HPFS/NTFS
/dev/sda2            4330        5849    12209400   83  Linux
/dev/sda3            7106        7296     1534207+   5  Extended
/dev/sda4            5850        7105    10088820   83  Linux
/dev/sda5            7168        7296     1036161   82  Linux swap / Solaris
/dev/sda6            7106        7167      497952   82  Linux swap / Solaris

Partition table entries are not in disk order

Thanks

---

### Post by bumanie on 2008-04-10
> sudo grub --> enter
> find /boot/grub/stage1
Please post output of second command

---

### Post by sandysandy on 2008-04-10
> It's almost back to normal after restoring my backup of menu.lst but it's missing Edubuntu 

u will have to make a manual entry for edubuntu in ur menu.lst file.

regards

---

### Post by toontastic on 2008-04-10
(hd0,1)
 (hd0,3)

---

### Post by bumanie on 2008-04-10
This should fix it
> sudo grub
root (hd0,1)
setup (hd0)
quit
try rebooting and it should work as before. If not check out this site [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
It's a lot to read, but very enlightening regrds grub and grub issues.

---

### Post by toontastic on 2008-04-10
That seems to have worked, thanks for that ! :KS

---

