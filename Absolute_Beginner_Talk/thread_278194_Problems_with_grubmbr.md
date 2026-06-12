---
title: "Problems with grub/mbr"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by mkelder on 2006-10-15
Previous install of win2k on a ntfs.  Used the partitioner with ubuntu to resize it for space for linux.  After install, grub lists windows but after it is selected for boot windows starts up and dies saying problem with drive.  I have installed ntfs read ability to ubuntu and can see everything there.  I tried using the windows install disk to repair the mbr but after choosing repair it tells me that it cannot dtect a HD even present and forces me to quit.

What the heck happend?  Somehow ubuntu removed the mbr with grub and there is no turning back.

My only option is to remove the HD and place it in a nother windows box and back up the files and format.  Or can any of you guys figure out a way to back track?

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5622    45158683+   7  HPFS/NTFS
/dev/sda2            5623        8896    26298405   83  Linux
/dev/sda3            8897        9039     1148647+   5  Extended
/dev/sda5            8897        9039     1148616   82  Linux swap / Solaris


title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by capn_hector on 2006-10-15
some times windows freaks out if you change its partition size.  id back up your data and do an over the top install.  that might fix it if not format and reinstall windows leaving your partition table alone.

---

### Post by mkelder on 2006-10-15
Thankyou for your reply.  Windows install will not let me do install or repair (saying no hd found).  Running windows off grub boots to the splash screen and then blue screens saying inaccesable boot device.

---

### Post by capn_hector on 2006-10-15
> **mkelder said:**
> Thankyou for your reply.  Windows install will not let me do install or repair (saying no hd found).  Running windows off grub boots to the splash screen and then blue screens saying inaccesable boot device.

you might try to use lilo instead of grub.  i dual booted using grub and had a lot of issues, i switched to lilo and every thing worked.  heres how to install it  [http://www.acm.uiuc.edu/workshops/linux_install/lilo.html](http://www.acm.uiuc.edu/workshops/linux_install/lilo.html)  and a small how to [http://www.tldp.org/HOWTO/LILO.html](http://www.tldp.org/HOWTO/LILO.html)  if that does not work, then a format and reinstall is your only option.

---

### Post by gn2 on 2006-10-16
If it's possible for you to add another hard drive, this may interest you: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by mkelder on 2006-10-16
Thanks for the info!

I used the super grub boot disk I found that lets you rewrite the mbr or lilo,grub...  It works great but after fixing the mbr I had the same issue!  I think you were correct thinking the partition resize messed up the windows install.

I guess my fix is to format and start over.

Anyone reading this thinking of installing ubuntu over windows I would suggest not to.

My guess is if you want both on a single HD then start with a fresh install of both OS's on partitions already sized and let the installer format which partition it wants to use.

---

