---
title: "Dual boot - how to reinstall Windows?"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by Laki on 2006-06-03
Hello!

I'm having dual-boot sistem with Ubuntu and XP. Now I would like to reinstall Windows partition with other version. How can I do this, without having problems with dual-boot after reinstalling XP? I want my Ubuntu partition as is now.

---

### Post by hajk on 2006-06-03
Installing a new version of Windows over a previous version is simple, just follow the instructions of your Windows install programme -- especially installing it in the right partition. Now, as you already indicate, the new Windows will overwrite the MBR, so that you won't be able to log in to your Ubuntu partition anymore, at least not without doing some work.

You need to boot a Linux liveCD, like the Dapper desktop (install) CD. You can also use a Knoppix CD (always handy to have lying around). Once booted, you must mount your Ubuntu partition(s), then do a chroot to the Ubuntu root partition. At this point it is as if you had booted into your Ubuntu partition, so now you can reinstall Grub to the MBR with the command sudo grub-install. Most people don't do this very often, so take your time reading up on how to use this command: check man-pages, search the forum, look at the wiki, you'll learn a lot this way.

Another way of doing this is to "sudo dpkg-reconfigure" the package that installs GRUB in the MBR... could it be the package grub itself?

When done, leave the chroot and reboot. Good luck!

---

### Post by hajk on 2006-06-03
Come to think of it, my above answer is possibly a bit cryptic for a new user. 
I collated the following detailed instructions from various places:

1. Start the restoration procedure by booting a Linux LiveCD, open a
terminal and obtain root privileges with the command 

sudo -i

(no password needed). 

2. Find the Ubuntu root partition from which GRUB is to be installed, e.g. 
dev/hda6. You may also have a separate /boot partition, like /dev/hda3; if not disregard all mention of it in what follows. If you have a SATA HD, then use /dev/sda. 

3. Create suitable mount points:

sudo mkdir /mnt/ubuntu
sudo mkdir /mnt/ubuntu/boot

and then mount the needed partitions and directories

sudo mount /dev/hda6 /mnt/ubuntu/
sudo mount /dev/hda3 /mnt/ubuntu/boot/
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo mount -o bind /proc /mnt/ubuntu/proc
sudo cp /proc/mounts /mnt/ubuntu/etc/mtab

4. Next ``chroot'' to the new working environment with

sudo chroot /mnt/ubuntu/ /bin/bash

From this point on, any files you modify will affect your Ubuntu
system -- you have left the safety of the LiveCD.

5. Restoring GRUB to the MBR is next done with

sudo /sbin/grub-install /dev/hda

There is no need to configure the GRUB menu if it was OK to start
with, GRUB will just use the existing file /boot/grub/menu.lst,
but now with the Windows XP partition added.

6. Done, now reboot.

---

### Post by WiLLiE on 2006-06-03
Thanks for the guide.

I just followed it and I get this errors:
```
root@ubuntu:/# sudo /sbin/grub-install /dev/sda
df: `/cow': No such file or directory
df: `/rofs': No such file or directory
df: `/rofs': No such file or directory
df: `/lib/modules/2.6.15-23-386/volatile': No such file or directory
df: `/media/usbdisk': No such file or directory
df: `/mnt/ubuntu': No such file or directory
df: `/mnt/ubuntu/boot': No such file or directory
df: `/mnt/ubuntu/dev': No such file or directory
df: `/mnt/ubuntu/proc': No such file or directory
Could not find device for /boot: Not found or not a block device
```

fdisk -l shows:
```
root@ubuntu:/# fdisk -l

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4501    36149248    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2647    21261996    7  HPFS/NTFS
/dev/sdb2            2648       14946    98791717+  83  Linux

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          10       80293+  83  Linux
/dev/sdc2              11         132      979965   82  Linux swap / Solaris
/dev/sdc3             133        4500    35085960   83  Linux
```

My dapper install is in sdc, and windows on sda.

/ and /boot is mounted correctly.

What now?

---

### Post by hajk on 2006-06-03
Hey WiLLiE, you're not the original poster! And with your multiple HD system, you should be really careful as to follow instructions meant for a simpler layout...

Now, the errors on the mount points: these mount points exist in the tree belonging to the liveCD, if there is no top level /mnt directory, then you should first make one, and then make the working sub-directories ubuntu and ubuntu/boot for mounting /dev/sdc3 and /dev/sdc1 on in that order.

Next, after chrooting to /mnt/ubuntu, there should already be a file called /boot/grub/menu.lst, made when you installed Dapper. Where did the Dapper installer install GRUB? in the MBR of /dev/sda? or /dev/sdc? Use the same location, or when in doubt read the GRUB man/info pages on what's best for you. Can't help you there without doing that kind of research myself...

---

