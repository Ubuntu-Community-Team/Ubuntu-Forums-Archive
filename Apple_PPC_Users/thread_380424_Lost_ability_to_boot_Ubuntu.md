---
title: "Lost ability to boot Ubuntu"
date: 2007-03-09
forum: Apple PPC Users
---

### Post by woopie49 on 2007-03-09
After updating my 10.3.9 OS with the latest updates on my primary HD, I cloned it over to my secondary HD which is dual boot with Ubuntu 6.10 on it.   I have now lost the ability to boot into Ubuntu.

When I "option" boot my Dual 1.42 G4 FW800 and select the Ubuntu icon, it will boot to the initial screen (Grub or Bootloader I think) but then reverts back to the "option" boot screen and hangs.

I can boot from the Live CD. 

I do not really want to re-install Ubuntu as I have it set up to how I want it and have reasonable skills in using Ubuntu.

I would appreciate any assistance in setting my problem right.

Thank you - Ron

---

### Post by Gannin on 2007-03-09
Take a look at this:

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

Scroll down to the part about restoring the GRUB boot loader, and see if that works for you.

---

### Post by maggot_brain on 2007-03-09
The above post has instructions that won't work on Apple PPC computers, (G4 is a PowerPC machine).  You need to reinstall Yaboot.  First of all you need to know which partition yaboot is installed on.  If you boot up with the live CD and go to System - Partition editor or something like that it will start up the Gnome partition editor.  The yaboot partition will be small and of an unknown partition type.  Find out the number of the partition that yaboot is installed on and make a note of it.

Then restart your computer and as SOON as it reboots hold down the apple key +command key + O + F.  This will take you to the openfirmware prompt.  It should be a grey screen with just 'ok' displayed and a cursor.  Assuming yaboot is on partition  2 (/dev/hda2 in Linux terms) type this at the openfirmware prompt:

boot hd:2,yaboot

Linux should then load.  Once you get into Linux go to a terminal or console and type this:

sudo ybin

The dual boot loader should now be working again!

---

### Post by woopie49 on 2007-03-10
Thanks for your replies guys.

As the default Live CD boot does not have System tools loaded or on the Live CD, I cannot use this to use that utility for partitions.

maggot_brain, if you, or some other kind person could post terminal/console instructions, I would be most grateful.

Ron

---

### Post by grazie on 2007-03-10
Boot with the Live CD. Restoring yaboot can be problematic. I'm assuming that your yaboot config is known to be good. However, given that you've lost yaboot working correctly already, this assumption could well be invalid. If you have any doubts, post your /etc/yaboot.conf, /etc/fstab and in a terminal the output of
```
$ sudo mac-fdisk -l
```
For illustration I'll assume your / root partition is /dev/hda5, but you need to detemine what it actually is yourself. If you're not sure, post the details above.
```
$ sudo su
$ mount /dev/hda5 /mnt
$ mount -o bind /proc /mnt/proc
$ mount -o bind /dev /mnt/dev
$ mount -o bind /sys /mnt/sys
$ chroot /mnt /bin/bash
```
You've now chrooted to your hd installation, so to re-install yaboot
```
$ ybin -v
```
If you get the 'blessed with holy penguin pee' message you've been successful. If not you need to post any error messages
```
$ exit
```
Umount the mounts and reboot
```
$ umount /mnt/sys
$ umount /mnt/dev
$ umount /mnt/proc
$ umount /mnt
$ exit
```
Voila

---

### Post by woopie49 on 2007-03-10
Thank you for your reply grazie

I'm not sure wheather the Ubuntu bootstrap is the same as the Apple bootstrap - here are the partitions on this hd

sudo mac-fdisk -l
/dev/hdc
        #                    type name                  length   base      ( size )  system
/dev/hdc1     Apple_partition_map Apple                     63 @ 1         ( 31.5k)  Partition map
/dev/hdc2     Apple_Bootstrap untitled                1954 @ 108931591     (977.0k)  NewWorld bootblock
/dev/hdc3     Apple_HFS Apple_HFS_Untitled_11  	      26797864 @ 262208    ( 12.8G)  HFS
/dev/hdc4     Apple_UNIX_SVR2 untitled                7617188 @ 108933545  (  3.6G)  Linux native
/dev/hdc5     Apple_UNIX_SVR2 Apple_HFS_Untitled_12   81609375 @ 27322216  ( 38.9G)  Linux native
/dev/hdc6     Apple_UNIX_SVR2 swap                    408019 @ 116550733   (199.2M)  Linux swap
/dev/hdc7     Apple_HFS Apple_HFS_Untitled_13         89374392 @ 116958752 ( 42.6G)  HFS
/dev/hdc8     Apple_Free Extra                        262144 @ 64          (128.0M)  Free space
/dev/hdc9     Apple_HFS Apple_HFS_Untitled_14         27846344 @ 206595288 ( 13.3G)  HFS
/dev/hdc10    Apple_Free Extra                        262144 @ 27060072    (128.0M)  Free space
/dev/hdc11    Apple_Free Extra                        262144 @ 206333144   (128.0M)  Free space
/dev/hdc12    Apple_Free Extra                        16 @ 234441632       (  8.0k)  Free space

Block size=512, Number of Blocks=234441648
DeviceType=0x0, DeviceId=0x0

ubuntu@ubuntu:~$ 

I really do appreciate your help - Ron

---

### Post by grazie on 2007-03-10
What disk drives do you have in the machine? You implied you have more than 1 hard drive. From the output it looks you have 3 OS X partitions and 1 or 2 linux partitions (not sure about /dev/hdc5). Does that match with what you expect? When you cloned is there any chance you selected a wrong partition?

Looks like your root partition is /dev/hdc4, but /dev/hdc5 description seems a little odd.

I think you need to post your /etc/fstab and /etc/yahoot.conf. To mount the HD root partition and get the details

```
$ sudo mount /dev/hdc4 /mnt
$ cat /mnt/etc/fstab
$ cat /mnt/etc/yaboot.conf
```
Then post the files here.
```
$ sudo umount /mnt
```

---

### Post by woopie49 on 2007-03-10
Hi grazie

This particular Mac has 3 HD's in it, but I've disconnected the other 2 to work on the Ubuntu HD.

The Ubuntu HD is a 120 gig HD and has 4 partitions on it, 2 Mac sys partitions (1 to "housekeep" the main sys partition), a data/general partition and the Ubuntu partition of 40 gig.

I originally partitioned this disk with 4 partitions (as above) with Disk Utility.  I would say the extra partitions shown in the mac-fdisk -l may be the result of me "blowing" the original install of Ubuntu and not correctly deleting the partitions I made for it before a successful install.

I will post back later to-day with the results of me trying to re-install Yaboot

Ron

---

### Post by grazie on 2007-03-10
With that extra info, I'd say that your Ubuntu root partition is /dev/hdc5, but I don't like the Apple_UNIX_SVR2 Apple_HFS_Untitled_12 description of it. Follow the instructions using /dev/hdc5 instead of /dev/hdc4 which I suspect is your original Ubuntu install.

---

### Post by woopie49 on 2007-03-10
Info for hdc4

sudo su
root@ubuntu:/home/ubuntu# sudo mount /dev/hdc4 /mnt
root@ubuntu:/home/ubuntu# cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd4
UUID=72d4a70d-2104-4a06-b700-9241ba6b406e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd6
UUID=8f1b708e-395a-44de-b9dc-26c97d4e0942 none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@ubuntu:/home/ubuntu# cat /mnt/etc/yaboot.conf
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

boot=/dev/hdd2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@1:
partition=4
root=/dev/hdd4
timeout=100
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hdd3

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet splash"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash"

# This entry automatically added by the Ubuntu installer for an existing
# Linux installation on /dev/hdd5.
image=/pci@f2000000/mac-io@17/ata-4@1f000/disk@1:5,/boot/vmlinux-2.6.15-23-powerpc
**label=hdd5-Ubuntu 6.06 LTS (6.06)
    root=/pci@f2000000/mac-io@17/ata-4@1f000/disk@1:5
    append="root=/dev/hdd5"
    initrd=/pci@f2000000/mac-io@17/ata-4@1f000/disk@1:5,/boot/initrd.img-2.6.15-23-powerpc
root@ubuntu:/home/ubuntu# 


**I note   "label=hdd5-Ubuntu 6.06 LTS (6.06)"  -a  previous Ubuntu install - this was a 6.10 install and no problems booting till I cloned the mac o/s.


Info for hdc5

sudo su
root@ubuntu:/home/ubuntu# sudo mount /dev/hdc5 /mnt
root@ubuntu:/home/ubuntu# cat /mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0
root@ubuntu:/home/ubuntu# cat /mnt/etc/yaboot.config
cat: /mnt/etc/yaboot.config: No such file or directory
root@ubuntu:/home/ubuntu# 

... and my re-install attempt, no go

I'll wait to see what you say, then I'll try again reinstalling yaboot, if to no avail the next time, I'll scrub the whole hd, clone the mac os partitions and put a fresh install of Ubuntu 6.10

I also tried what maggot_brain posted thru openfirmware but to no avail.

---

### Post by spikee on 2007-03-10
For my powerbook and iMac I used this dual boot guide which works like a charm. 
[http://blogs.sun.com/richb/entry/powerbook_dual_boot:_macosx_tiger](http://blogs.sun.com/richb/entry/powerbook_dual_boot:_macosx_tiger)

---

### Post by grazie on 2007-03-10
Well /dev/hca4 does indeed look like your old Ubuntu installation and the config is horribly out of date. 

However, the missing /etc/yaboot.conf from /dev/hdc5 is odd and the misssing swap file details in /etc/fstab is again unexpected. Any ideas what could have happened? Did you use to boot this partition form another disk? Reconstructing a new yaboot.conf from scratch is certainly possible but would require further details from you, and the thread isn't the easiest way communicate. 

If the ubuntu install is worth saving, I'd do the following. As the /dev/hdc4 partition is out of action I'd do a temp install of ubuntu on there. Once installed, from there you can more easily see what's needed to recover /dev/hdc5 or you could just secure any important data. A complete wipe the HD really isn't necessary. I think your scenario is an execellent example of the benefits of keeping data and OS partitions separate.

Of course you may still be able to boot from Open Firmware by following the the details decribed in [chapter 6]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml"), [chapter 9]("http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch9.en.shtml") and other chapters.

---

