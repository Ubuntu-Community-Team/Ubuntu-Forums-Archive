---
title: "Ubuntu won't boot (properly)"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by seeknowsage on 2007-07-19
My Ubuntu machine refuses to boot properly after I removed an ipod shuffle connected to it before ejecting it. At least that's the only thing I can think of that may have given rise to this problem. When I attempt to boot, the system apparently hangs on the black screen with the ubuntu logo and loading bar filled at approximately 1% (it never moves). However, after about 5 minutes, the system boots and I am presented with a screen that states the following:

> BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3)  Built in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)_


If I boot in recovery mode, the system apparently hangs here:
> [17179582.100000] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[17179582.100000] sda: Write Protect is off
[17179582.100000] sda: assuming drive cache: write through
[17179582.100000] SCSI device sda: 495616 2048-byte hdwr sectors (1015 MB)
[17179582.100000] sda: Write Protect is off
[17179582.100000] sda: assuming drive cache: write through
[17179582.100000]  sda: unknown partition table
[17179582.100000] sd 0:0:0:0: Attached scsi removable dsik sda

After a few minutes, this screen adds the following:
> Done.
ALERT! /dev/hda1 does not exist. Dropping to a shell!


I am then presented with the initramfs message and command prompt above. I've tried booting both with and without the ipod shuffle attached to no avail. This morning, everything was working just fine and as I've mentioned before, the only thing I have changed is the removal of the ipod from the system. Can anyone help me with this (assuming it is something that may be fixed)? Thanks.

---

### Post by twiceasworn on 2007-07-19
Are you able to get to the command line?  If you are I would take a look at your logs.  Though from the error message stating that /dev/hda1 doesn't exsist worries me.  If you can get to /var/log/messages or /var/log/syslog I would suggest looking in those to see if they hold anything interesting.

---

### Post by deadgobby on 2007-07-19
That is a new one to me. Here  may be the Opener of The Way.
[http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error](http://www.utheguru.com/solution-ubuntu-linux-binsh-cant-access-tty-job-control-mode-off-error)

---

### Post by rickycodie on 2007-07-19
the error about hda1 is talking about the hdd not being found, maybe you could remount it from the command line, and that would fix that.

cd to the hdd and type;

sudo mount.

hope that helps.

---

### Post by Midahed on 2007-07-19
I'm guessing, but it seems to be saying that /dev/hda1 doesn't exist - i.e. it can't find that partition.

I'd boot the live CD and then see if you can 'see' your drive.  Open a terminal session and try something like fdisk -l

If that reports that it can see the drive and if the partition layout looks like it should, I'd try to mount the drive and see if it's accessible.

Mike

---

### Post by seeknowsage on 2007-07-19
Thank you all for your replies! I am trying your suggested tips right now. (Well, right after I eat lunch, rather, which will be in about 15 min ;). I'll let you all know how it goes.

---

### Post by Corvias on 2007-07-19
Are you using GRUB? A few moments after you turn your PC on, You'll see something like "GRUB Loading.. Hit esc for menu" (or some thing like that. If you hit escape, you should receive the list of available kernels/OS's you can boot into. Usually the topmost one is the default. Select it, and hit 'e'. this will show you the actual GRUB command that is executed if/when that item is used.

Post that line here along with how many HD's you have installed and how they are partitioned. Then we'll see if we can get this figured out. 

Corvias

---

### Post by seeknowsage on 2007-07-19
> **(initramfs) cd /var/log/messages**
/bin/sh:  cd: can't cd to /var/log/messages
**(initramfs) cd /var/log/syslog**
/bin/sh:  cd: can't cd to /var/log/syslog
**(initramfs) ls**
dev bin etc modules scripts usr proc var
root conf lib sbin init sys tmp
**(initramfs) sudo mount**
/bin/sh: sudo: not found
**(initramfs) mount**
none on /sys type sysfs (rw, nosuid, nodev, noexec)
none on /proc type proc (rw, nosuid, nodev, noexec)
udev on /dev type tmpfs (rw)

I tried following the instruction on utheguru, but they didn't help. )=

I'll try the LIVE cd mount approach now.

Also, no, I am not using grub either.

---

### Post by seeknowsage on 2007-07-19
Below is what I get when I boot with the live cd.

> **ubuntu@ubuntu:/var/log$ sudo mount**
unionfs on / type unionfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda on /media/ipod type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=999,gid=999,umask=077,iocharset=utf8)

**ubuntu@ubuntu:/var/log$ fdisk -l**
Note: sector size is 2048 (not 512)

Disk /dev/sda: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sda2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sda3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sda4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Note that I tried removing the ipod shuffle and running fdisk again, but when I did this nothing was returned. Additionally, it appears as though ubuntu wiped the songs on my ipod shuffle. This is starting to get frustrating, but primarily because just yesterday my main computer's psu died and took the cpu with it. Now my backup Ubuntu computer isn't playing nice. )=

---

### Post by seeknowsage on 2007-07-19
[[IMG]http://img527.imageshack.us/img527/1604/screenshotus5.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshotus5.png)
[[IMG]http://img381.imageshack.us/img381/1803/screenshot1nc2.th.png[/IMG]](http://img381.imageshack.us/my.php?image=screenshot1nc2.png)
[[IMG]http://img527.imageshack.us/img527/3604/screenshot2ln3.th.png[/IMG]](http://img527.imageshack.us/my.php?image=screenshot2ln3.png)


These are the screenshots from the device manager when I boot into the Live CD. Can anyone help with this or am I just screwed?

---

### Post by Midahed on 2007-07-19
I'd forget the iPod for the moment - it's just a diversion.  If you can't boot the system, the ability to connect an iPod or not is of little relevance :)

Your first screenshot seems to show a Maxtor hard disk with an ext3 partition on it.  Is that what you're trying to boot from?

However, the results of your mount command and fdisk -l seem to indicate that the system is not seeing a hard drive at all.  It lists your iPod as /dev/sda but, unsurprisingly doesn't understand it's partition table :D  Seeing you're presumably not trying to boot off the iPod, that doesn't matter.

I'd concentrate on finding out why you don't have a hard disk.  Open up the case and check cables, etc.  Can you hear the drive spin-up when you power-on the system.  Is the drive recognised by the BIOS, or is it not even being detected at that level.

Mike

---

### Post by seeknowsage on 2007-07-19
Thanks for your reply. And trust me, the ipod has since been long forgotten. (=

As it is, the hard drive is connected and is recognized in the BIOS. I've attempted to change the boot location in the bios to various locations, but the same result is achieved each time: I get to the black screen with the ubuntu logo and the loading bar stalls before it even moves. After a few minutes, I get the "can't access tty" error message.

---

### Post by Midahed on 2007-07-19
If you boot from the system (not the live CD) and you get as far as seeing the Ubuntu logo, then Linux must be recognising your drive - otherwise you wouldn't get that far.  I don't understand why you cannot see it when you do fdisk -l

What do you get if you...

cat /proc/partitions

It's way past my bedtime, but I'll look to see how you're getting on tomorrow.

Mike

---

### Post by seeknowsage on 2007-07-19
Mike,
     Thank you very much for your help! When I run the live cd, this is what I get: 

> 
**ubuntu@ubuntu:~$ cat /proc/partitions**
major minor  #blocks  name

   3     0   80043264 hda
   3     2   37664392 hda2
   3     3    2096482 hda3
   3     4     514080 hda4
   7     0     647432 loop0

I got those results after running **sudo mount -t ext3 /dev/hda2 /mnt** from the command line.

---

### Post by seeknowsage on 2007-07-19
I forgot to mention in my last post that when I do a [B]sudo mount -t ext3 /dev/hda2 /mnt
[/B], the Disk Usage Analyzer recognizes my hard drive along with my file directory, as shown in the picture below. However, I still can't get my system to boot from this drive without getting the aforementioned errors. )=

[[IMG]http://img358.imageshack.us/img358/231/screenshot1bl6.th.png[/IMG]](http://img358.imageshack.us/my.php?image=screenshot1bl6.png)

---

### Post by Midahed on 2007-07-19
Well, the system obviously recognises the drive just fine.  For the life of me, I cannot understand why it didn't show up when you did fdisk -l

Anyway, that doesn't matter now...

Can you cat /etc/fstab and post the output so that we can see which partition is which on hda.

The slightly strange thing is that, according to cat /proc/partitions you don't have a partition 1 showing.  Is there any reason you can think of why this might be the case?  There might be a perfectly good reason why, but it would be handy to know what it is.

By the way, apart from plugging-in the dreaded iPod, did you do anything else that might have triggered the current problem?  Time to confess, right now, if you did ;)  Can you think of anything at all that might be linked to this?

Finally, I think you said earlier that you are not using GRUB.  What boot loader are you using instead - it is looking like the problem is in that area.

Now it really is my bedtime, so I won't be responding again tonight....

Mike

---

### Post by seeknowsage on 2007-07-19
After digging around a hazy memory for a bit, I just now realized that I had Ubuntu do an update this morning when my system was still functioning. I didn't scrutinize what all security updates were included, but now that I think about it, I do receive a few different kernels to choose from when now booting whereas I previously received two options. 

The new kernel is *-12 and the old ones were *-11 and *-10. I've tried booting into *-11 a few different times, but to the same error messages I've described above. Moreover, I said earlier I didn't have grub installed, but that was out of my own ignorance and I apologize about that. I DO have grub installed. Sorry about that. )=

Oh, and I'm running Edgy.

In response to Mike's questions (sorry, I didn't initially see your post above!):
> **root@ubuntu:/# cat /etc/fstab**
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0 
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda4 /media/hda4 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hda3  none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0


And the only reason I can think of for not having a partition 1 showing is because I originally partitioned the hard drive down the middle with the intention of installing windows on the first partition and Ubuntu on the second. As it is, I only got around to installing Ubuntu.

---

### Post by seeknowsage on 2007-07-19
It's back! Apparently when I did that update (or screwed with the ipod, one) it renamed my hd's. I had to edit the menu.lst file in /boot/grub/ to boot from hda2 as opposed to hda1. Is there any way to change this back or should I just leave well enough alone? In looking into the "tty" problem after creating my first post, I see that it is somewhat widespread and apologize for not reading up about it before hand. )=

---

### Post by Midahed on 2007-07-19
OK, that makes sense.  You have hda2 as your root partition and hda3 as swap.

I'm absolutely sure this is a GRUB problem.  Can you cat /boot/grub/menu.lst and post the output.  

Before your system freezes on the logo screen, you probably get a number of boot options appearing as a menu.  If you scroll down towards the bottom of the output from menu.lst, you'll be able to see the data that is the basis of that menu.  Take a look at the lines that begin 'title' - you should be able to relate these to the choices you get when booting.  When you post the output from menu.lst, can you say which titlle line you are selecting as your boot option - I mean the one that _recently_ used to work, not some other entry that might be an earlier kernel from a while ago.

Now I really am going...

Mike

---

### Post by Midahed on 2007-07-19
Ah, that's good news.  Got there on your own in the end:)

As your root partition is hda2, that's the way it has to stay unless you re-partition your disk and do a lot of messing about.

I suspect the reason the update stuffed your menu.lst is because it has an incorrect entry elsewhere and this is _telling_ the update process to use the wrong partition numbers for it's new entries.

We can confirm that (and correct it) if you post the menu.lst output.

Mike

---

### Post by seeknowsage on 2007-07-19
Here is my menu.lst file:

> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password DELETED 
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password DELETED

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f50e1bfb-f7bc-4c08-9aec-1604900d23a9 ro
# kopt_2_6=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-12-generic
boot

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
#title		Microsoft Windows XP Professional
#root		(hd0,1)
#savedefault
#makeactive
#chainloader	+1

I tried doing the *-12 kernel after renaming the hd in the menu.lst file, but it booted to a failed xorg.conf file, so instead of editing it or resorting to a back up, I just booted into *-11, which is the kernel I normally use.

---

### Post by seeknowsage on 2007-07-19
Weird, it changed the post order around. Regardless, thank you very much for your help Midahed!

---

### Post by Midahed on 2007-07-19
I had a quick look at your menu.lst and expected the groot entry to be wrong, but it looks OK.

I'm not that familiar with GRUB so I can't be sure without checking the manual, but I'd be inclined to check the two kopt lines:-

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
**# kopt=root=UUID=f50e1bfb-f7bc-4c08-9aec-1604900d23a9 ro**
**# kopt_2_6=root=/dev/hda1 ro**

## default grub root device
## e.g. groot=(hd0,0)
**# groot=(hd0,1)**

I'm not sure how the kernel optiions are applied, but I'd run the command blkid so that the system tells you all your partition UUIDs and check that the UUID in the first of the two kopt line matches that of your root partition (hda2).  Alternatively, you could just change the line to:-

# kopt=root=/dev/hda2 ro

But it would be better to see if there's a UUID mis-match first (otherwise you'd be fixing a non-existent problem)

Also, the other highlighted kopt line looks wrong - I think it should be:-

# kopt_2_6=root=/dev/hda2 ro

As I say, without reading the manual I'm not sure how the kopt entries affect the application of updates to the menu.lst file, but it's worth trying these or at least looking at the GRUB manual [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Goodnight!

Mike

---

