---
title: "Can't add XP to Grub"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by Reese268 on 2006-11-05
Hey,

I installed Ubuntu on it's own partition, and for whatever reason it did not place XP into Grub.  I am trying to add it to there, but am unable to.  To make things worse, I also cannot access the internet on that computer due to my wireless card not working (but that's not really what I want help on at the moment).

XP is on the first primary partition.  What do I need to add to Grub to enable it to boot to XP?

---

### Post by Turin Turambar on 2006-11-05
Go back to Ubuntu and type in Terminal:

sudo gedit /boot/grub/menu.lst

and try adding this (copy/paste) to the end of the menu.lst file.

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Hope it helps...

---

### Post by MasterOfDisaster on 2006-11-05
Pretty sure that you need to specify what partition you installed Windows on.
The above entry might work, depending on where you installed XP, but check what partition Windows is on and Grub partition naming conventions to be sure.

---

### Post by samknex on 2008-05-16
I am having about the same problem. I sure hope that somebody notices this. here is my sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00bbbca2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        1338      979965   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05316498

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9964    80035798+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    c  W95 FAT32 (LBA)

Now, the first disk, the 200gb one has ubuntu installed on the second partition with the third as swap. Then XP is installed on the second one. 

Ignore the third one.

_Now, when I go to add XP, I modify it to look like this:_

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Microsoft Windows XP Home
root		(hd1,0)
savedefault
makeactive
chainloader	+1

I think that this is correct, but im not sure. Now when I go to boot, I open up the boot menu and try to click on windows XP. It pulls up the loading setup... or something. I can't remember what it says. But it just hangs there. There is 0 hard drive activity and it is not loading. Why??!?!

---

### Post by meierfra. on 2008-05-16
try

title Microsoft Windows XP Home
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1


if that does not work


title Microsoft Windows XP Home
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
savedefault
makeactive
chainloader +1

---

### Post by 123456X on 2008-06-02
hey guys I'm having a sorta similar problem...

so i had Ubuntu 7.10 installed and wanted to run xp as a dual boot sys on one hdd.
i had xp installed and running but it wouldn't recognize ubuntu and kept booting to xp. 

i used the tutorial found at [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

everything went great until i got the "reinstalling grub to the mbr" portion. so i used the recovery console to reinstall the grub. i loaded gparted and checked the "boot" flag option for the ext3 partition and ubuntu booted fine. 

now i restarted and it will only boot to ubuntu but it freezes at the loading screen with no orange on the loading bar. it goes into busybox which i'm not at all familiar with.

what's worse is i went back into gparted and checked the boot option to run the windows partition and it still trys to load ubuntu. ubuntu is my first partition and windows xp is the second 3rd is swap file (?)

i'm running an ibm netvista 8303

if someone could help i would love that!

---

### Post by meierfra. on 2008-06-02
First of all grub does not use boot flags, so the position of the boot flags is completely irrelevant.

Boot from the LiveCD. Open a terminal and type

```

sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
sudo cp menu.lst menu.lst.bu
gksudo  gedit menu.lst
```

This opened and backup-ed the file "menu.lst" (lst is short for list)

Look for the first appearance of

title Ubuntu......
root (hd0,0)
kernel /vmlinuz...   root=UUID=some_long_number  ... quiet splash
initrd ....

Change "root=UUID=some_long_number" to "root=/dev/sda1"  (This might solve your booting problem for Ubuntu, but I'm not sure)

Remove "quiet" and "splash" (this way you might be able to see some useful error messages during boot up)

To be able to boot into  XP change


"timeout 3" to "timeout 10"

and 

"hiddenmenu" to "#hiddenmenu"

Also use this for your Windows Item

title Windows XP
root (hd0,1)
makeactive
chainloader +1

this assume that XP is the second partition, use (hd0,2) if it is the third (type "sudo fdisk -l" to find out, or look at the partitions with the partition editor)

Save the file and reboot.

If you are still having problems, report any error messages you are getting during boot up.

Also post the output of 

```
sudo fdisk -l
```
```
 sudo blkid
```

and the content of "menu.lst"

---

