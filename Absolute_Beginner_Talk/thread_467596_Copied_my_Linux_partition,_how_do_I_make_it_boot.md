---
title: "Copied my Linux partition, how do I make it boot?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-07
I copied my Ubuntu Linux partition from a 20GB partition to an 80 GB partition.  Now, how do I tell the boot loader that its there and make it selectable in the Boot menu.

I used Norton Ghost to clone my Ubuntu partition to a bigger partition.

Any insight on this is appreciated.

Carl

---

### Post by ambush_xx on 2007-06-07
fdisk -l
find out the number of your linux partition

/boot/grub/menu.lst
change the number there acordingly.

---

### Post by logos34 on 2007-06-07
you'll need to edit your partition #'s in /etc/fstab also.

---

### Post by cwmoser on 2007-06-07
I found a URL that suggested to do this:

sudo grub

grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd1,2)

grub> root (hd0,5)

grub> setup (hd0)

grub quit



Then I chickened out and aborted this.  I have 3 Linux partitions and an XP partition and want all of them bootable from the menu.  The (hd0,5) is the newest partition that I cloned using Norton Ghost -- it is one that I would like to add to the menu so I can select it to boot.

Should I go ahead and do this?

Carl

---

### Post by logos34 on 2007-06-07
That look right based on the info you've provided.  But make sure your files are edited correctly otherwise it won't boot properly.

Post those files if at all unsure so we can take a look.

So the cloned root partition is on hda6?

---

### Post by cwmoser on 2007-06-07
One more thing:

/dev/sda3 is my older Ubuntu 6.10

/dev/sdb3 is my Ubuntu 7.05 in a 20GB partition

/dev/sda6 is my Ubuntu 7.5 that I cloned to an 80GB partition that I would like to boot.

Carl

---

### Post by logos34 on 2007-06-07
oh, its a sata drive.  

Does your menu.lst use the UUID number scheme?  If so it might cause problems.

---

### Post by cwmoser on 2007-06-08
Yes, my menu.lst does use teh UUID schema.


Here is my /boot/grub/menu.lst:
=========================================


default			0

title		Ubuntu, kernel 2.6.21.1
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.21.1 root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro quiet splash
initrd		/boot/initrd.img-2.6.21.1
quiet
savedefault

title		Ubuntu, kernel 2.6.21.1 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.21.1 root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro single
initrd		/boot/initrd.img-2.6.21.1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-386
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-386 root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro single
initrd		/boot/initrd.img-2.6.20-15-386

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=5d29954c-f223-45ef-8ada-41fcd820f008 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,2)
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
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.17-10-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.17-10-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda3 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu 6.10 (6.10) (on /dev/sdb2) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2 
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



# HERE IS WHAT I TRIED -  IT DOES NOT APPEAR IN THE BOOT MENU THOUGH:

title		Ubuntu, kernel 2.6.21.1 on /dev/sda6 80GB Partition
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.21.1 root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.21.1
quiet
savedefault

---

### Post by cwmoser on 2007-06-08
BTW, I saw a post mentioning to "Install Grub from the Live CD" -- do you think that would solve my problem with getting my new partition and my other partitions to appear bootable in the boot menu?

Carl

---

### Post by logos34 on 2007-06-08
> # HERE IS WHAT I TRIED - IT DOES NOT APPEAR IN THE BOOT MENU THOUGH:

title Ubuntu, kernel 2.6.21.1 on /dev/sda6 80GB Partition
root (hd0,5)

If you added that to the menu.lst on the cloned partition, then of course it won;t show up because its still using the (unedited) menu from sdb3.  It'll show up after you reinstall grub pointing to root on (hd0,5) /dev/sda6.


What happened here:
> # This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title Ubuntu 6.10 (6.10) (on /dev/sdb2) (on /dev/sda3)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sdb2
savedefault
boot
???

Your menu.lst is a bit confusing.   Not sure what's the deal with the two winXP pro partitions of sda1 and sdb1 (same partition but switched boot order? which would explain the 'map' lines).

> BTW, I saw a post mentioning to "Install Grub from the Live CD" -- do you think that would solve my problem with getting my new partition and my other partitions to appear bootable in the boot menu?

You only need to use the live cd if you can't boot into any ubuntu partitions.  (see below)

I know you want to get this thing going--it's just that I'm not exactly sure what happens to the uuid designations when you clone a root partition (to another disk in this case).  You can't have the original and the clone with the same uuid (or so it would seem).  If there's a discrepancy, you won't be able to boot the new one.   So, you can either edit the uuid on the cloned partition or just replace them with the 'root=/dev/sda6' format (like tha other kernels).  You'll also have to edit /etc/fstab to use the (new) uuid or replace with '/dev/sda6', or else it won't mount.

To check the (new?) UUID: 

**blkid**
OR
**ls -l /dev/disk/by-uuid/**

Then edit your files accordingly, or just change to the /dev/sda6 format.

Or if you just want to jump in and try booting without editing anything, do the above procedure you aborted and see if that works.  If it doesn't, then you will either have to try to temporarily edit the menu.lst just enough to get it to boot (after which you can get into your files to make the change permanent), or reboot from the live cd to fix things.  If it won't boot the kernel on sda6, hit Esc key, go back and hit 'e' to edit the highlighted kernel, then manually replace the UUID in the 'kernel' line with 'dev/sda6'.  It may find /boot/grub but it still may not mount.  In that case you will have to boot from the live cd to get to your fstab.

Using the live cd, to edit any files you will have to mount sda6 first:
[B]sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda6 /mnt/ubuntu
cd /mnt/ubuntu/boot/grub
sudo gedit menu.lst[/B]

and

**cd /etc/fstab**
sudo gedit fstab

---

### Post by dannyboy79 on 2007-06-08
when you clone a drive, it takes along the same UUID just so you are aware, so both your drives WILL have the same UUID.

---

