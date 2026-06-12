---
title: "Just installed ubuntu 7.10 amd64, but boots to winxp instead"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by snkmad on 2007-10-23
What change do i need to make to boot grub/ubuntu before winxp? The way it is, its going straight to winxp, doesnt load grub. Gotta a SATA drive, on 1st partition winxp, 2nd partition ubuntu 7.10 amd64, PATA drive is backup only, in ntfs format.

Looks like grub got installed on the PATA drive, even though ubuntu is on the SATA one.


sudo fdisk -l :

> Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0299bdb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9725    78116031    7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd4c6d4c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223        9603    35190382+  83  Linux
/dev/sda3            9604        9729     1012095   82  Linux swap / Solaris

My device.map:

> (hd0)	/dev/hda
(hd1)	/dev/sda

my menu.lst:

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8321aeea-e905-4093-950d-7a7735c8b5d7 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8321aeea-e905-4093-950d-7a7735c8b5d7 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

Just need to know what changes and in which files i need to make to boot to ubuntu. And installing grub into a floppy is not an option, dont have floppy drive anymore.

---

### Post by jdfreshwater on 2007-10-23
Try changing the order of your boot drives in bios.  It may be that grub has been installed on the other drive.  This may be the easiest fix that I can think of.  At that point you should see if it has installed grub correctly but on the wrong disc.

---

### Post by snkmad on 2007-10-23
Well the problem in having grub on the other HDD, sometimes i take it out and go to friends houses to carry some files.

How do i completely unninstall and install back grub? This time ill take a look if i can set it to sda instead of hda.

---

### Post by Daveth on 2007-10-23
this will help you find any lost grubs

[http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell](http://users.bigpond.net.au/hermanzone/p15.htm#GRUB_shell)

---

### Post by spur on 2007-10-23
If using  the super grub disc does not work the cause of your problems may be that grub does not like the mix of sata and ide. To get the mix to work every time you boot, the boot data and grub need to be on the ide drive. I also put  my '/' partition on the ide as well to make sure.

---

### Post by meierfra on 2007-10-24
Can you set the bios to boot from PATA drive? That should fix your  problem.

If not try   this:

```
sudo grub
```

at the grub prompt type

find /boot/grub/stage1

the output  should be (hdx,1)  with x=0 or 1.

type

root (hdx,1)

setup (hdx)

quit

In menu.lst change all (hd1,y) to (hd0,y)  and remove the two "map"-lines in the Windows item.

---

### Post by snkmad on 2007-10-24
Thanks, im gonna try this after lunch and report back.

EDIT: It worked!! Really thanks guys, and specially meierfra.
Im gonna right this down and put together my ubuntu cd, in case i need to reinstall my system again.
You should put that on the wiki. Really simple way to fix this problem.

---

