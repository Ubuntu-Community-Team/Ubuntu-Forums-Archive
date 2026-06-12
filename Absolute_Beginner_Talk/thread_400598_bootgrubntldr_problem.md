---
title: "boot/grub/ntldr problem"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by corres on 2007-04-03
Hi all!

I've problem with booting previously installed windows xp.

Situation exactly:

I'm trying to install 3 OS's on one disk: 
 - Win XP
 - WinXP
 - Ubuntu. 
At last I've Ubuntu (6.1 x64) installed, so in the MBR there's GRUB. At startup the GRUB shows a menu, from which I can select Ubuntu, and the 2 WinXPs. The Ubuntu boots when I select it, but none of the windows does. When I select windows, then I get the following error message:
Error 12: Invalid device requested.
I've been searching on the net for 2 hours, but didn't find anything useful.
My hard drive has the following paritions (in order):
1. a primary partition, 32 MB, ext2 (mounted: /boot)
2. an extended partition, which contatins
    1. a logical partition 5GB, WinXP1, NTFS
    2. a logical partition 20GB, WinXP2, NTFS
    3. a logical partition 1 GB, linux swap (mounted as /swap)
    4. a log. part. 19GB, linux root, ext3 (mounted: /)
    5. a log. part. ? GB, windows data (mp3, film, etc), NTFS
    6. a log. part. 2 GB, windows+linux fat32 for my works.

I also copied ntldr and ntdetect.com to both of the windows roots.

----------------------------------------
/boot/grub/menu.lst contains:
----------------------------------------
default		0
timeout		10

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda10 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda10 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows NT/2000/XP
root		(hd0,4)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda6
title		Windows NT/2000/XP
root		(hd0,5)
savedefault
makeactive
chainloader	+1

Please help me.

---

### Post by chewearn on 2007-04-04
You have placed both WinXPs in logical partitions.  From what I know, that might not be possible (don't quote me though, I'm not entirely positive  :mrgreen: ).

Maybe it will work if you have both WinXPs in sda1 and sda2 (primary partitions), then sda3 extended partition containing logical partitions for your linux stuff.

---

