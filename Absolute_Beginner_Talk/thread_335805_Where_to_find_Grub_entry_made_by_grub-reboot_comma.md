---
title: "Where to find Grub entry made by grub-reboot command"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by habtish on 2007-01-10
Hello,

In my previous posts, I have stated that I have a broken PS/2 port for my keyboard connection on my tower and couldn't do anything when the computer starts as my BIOS doesn't read [is not enabled to support] legacy USB devices.
fortunately before all this happend, I had set my default OS in the Grub menu as Ubuntu, which meant when I start my computer, BIOS will complain about missing keyboard, grub comes in and loads the default OS, dual booting is impossible as I can not use my keyboard to choose what OS I want.

Well today someone brought the idea of using grub reboot for a "one time" change in the default OS, therefore I did:
```
sudo grub-reboot 3
```The XP entry I was trying to load into was 4 and not 3, so now when i try to boot my computer i get the following```
 error: 18 Selected cylinder exceeds maximum supported by BIOS
Press any Key to continue...
```ofcourse I can not press anyting because my keyboard is not active.

I am now using a Dapper Livecd and have mounted my ubuntu partition. I want to delete the onetime default OS but can not find it. Here is my Menu.lst
```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=03f1f827-6338-42e4-9224-b1ebdf86f4eb ro
# kopt_2_6=root=/dev/hdb2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title        Ubuntu, kernel 2.6.17-10-generic
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro 
initrd        /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title        Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root        (hd1,1)
kernel        /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 ro single
initrd        /boot/initrd.img-2.6.17-10-generic
boot

title        Ubuntu, memtest86+
root        (hd1,1)
kernel        /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title        Microsoft Windows XP Home Edition
root        (hd0,1)
savedefault
makeactive
chainloader    +1




```This is the menu.lst from the ubuntu partition I mounted at /media/ubuntu under /media/ubuntu/boot/grub/menu.lst

How do I get grub to load ubuntu again? Where did it save the default OS I passed when I invoked grub-reboot??
Please help !

---

### Post by erik_boi on 2007-01-10
This sounds like the same problem that is addressed in this thread [http://ubuntuforums.org/showthread.php?t=334748]("http://ubuntuforums.org/showthread.php?t=334748")

It seems as if you may need to reinstall grub, they outline it in that thread but there is a guide that goes more in depth here [RecoveringGrub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

Be certain to use the right drive lettering an partition numbering and everything should go smoothly. Also, make a copy of your menu.lst so you can put everything back how it was before.

On a side note you may try to chroot into your ubuntu partition from the live-cd and "grub-reboot (whatever you want)" I would have tried myself but grub-reboot has absolutely no effect on my computer whatsoever (from the running os or the chrooted one).

---

### Post by habtish on 2007-01-11
> **erik_boi said:**
> This sounds like the same problem that is addressed in this thread [http://ubuntuforums.org/showthread.php?t=334748](http://ubuntuforums.org/showthread.php?t=334748)

It seems as if you may need to reinstall grub, they outline it in that thread but there is a guide that goes more in depth here [RecoveringGrub ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")


I just saw this thread, I was searching for Grub and not grub-reboot before posting here. It is very helpful, thanks
> 
Be certain to use the right drive lettering an partition numbering and everything should go smoothly. Also, make a copy of your menu.lst so you can put everything back how it was before.
On the drive lettering, My windows partition is on hda1, so I am assuming the MBR would be on /dev/hda?
> 
On a side note you may try to chroot into your ubuntu partition from the live-cd and "grub-reboot (whatever you want)" I would have tried myself but grub-reboot has absolutely no effect on my computer whatsoever (from the running os or the chrooted one).I have never tried the chroot option, however, I can read-up on it and give it a try. Not on my computer ATM, once I get home, I will backup my menu.lst (emailed a copy of it to myself as a txt file yesterday) and try the grub-install. But when doing this from a livecd, how does it know to use the mounted /boot partition (/media/ubuntu/boot) and not the livecd boot partition (/boot)
Sorry if this is annoying, still learning by way of my screw-ups I guess

---

### Post by confused57 on 2007-01-11
You probably don't have a separate /boot partition, unless you manually partitioned and selected to have one...the default install is for no separate /boot partition, therefore you "shouldn't" need to run:
mkdir /mnt/work/boot
or
sudo mount /dev/hda3 /boot/

unless you do have a separate /boot.

The directory before the $ prompt should change to let you know you are in the chroot environment of your installation.

---

### Post by erik_boi on 2007-01-11
If you have the standard installation use these steps from the previous link to reinstall grub. The only thing different is in step 4, you won't have a /boot partition so you point it at the root (/) partition and use the proper number corresponding to your partitioning.
```
Using the Desktop/LiveCD and Overwriting the Windows bootloader

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).
3. Type "sudo grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", or whatever your harddisk number is.
6. Quit grub by typing "quit".
7. Reboot.

```

> On the drive lettering, My windows partition is on hda1, so I am assuming the MBR would be on /dev/hda?
Yes.
> But when doing this from a livecd, how does it know to use the mounted /boot partition (/media/ubuntu/boot) and not the livecd boot partition (/boot)

As far as using chroot and issuing the grub-reboot command, it is probably not going to work (me making assumptions based on the other thread) and reinstalling grub is just easier. I am not sure what I was thinking last night when I suggested that.

Anyways, chroot is a program that allows you to change the root directory for the terminal that you are using. For example, in your case if the ubuntu partition is mounted on /media/ubuntu, issuing "chroot /media/ubuntu" will cause any further commands run on that same shell to be relative to /media/ubuntu. So if you enter "vim /boot/grub/menu.lst" you will be using the vim program that is located at /media/ubuntu/usr/bin/vim and editing /media/ubuntu/boot/grub/menu.lst.

---

### Post by habtish on 2007-01-11
> **erik_boi said:**
> 
Anyways, chroot is a program that allows you to change the root directory for the terminal that you are using. For example, in your case if the ubuntu partition is mounted on /media/ubuntu, issuing "chroot /media/ubuntu" will cause any further commands run on that same shell to be relative to /media/ubuntu. So if you enter "vim /boot/grub/menu.lst" you will be using the vim program that is located at /media/ubuntu/usr/bin/vim and editing /media/ubuntu/boot/grub/menu.lst.
That is handy.. I had wanted to listen to my mp3 yesterday while in the livecd and didn't want to go about installing extra codecs again.. and tried to do a ```
/media/ubuntu/usr/bin xmms 
``` which of course failed because it couldn't load some libraries. If chrooting is something that would enable me to run these apps even when they're just on a mounted drive, then it is very cool. 

The whole drive lettering thing looks confusing with the grub-install, but I will work through this when I go home and update you.... Thanks so much in following up with this and replying

---

### Post by confused57 on 2007-01-11
When you're finished chrooting you might want to exit the chroot environment & unmount the mounted directories, then reboot... see the end of this link(your mounted directories would be different):
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)
On second thought, the Ubuntu live cd probably automatically unmounts all the partitions, therefore you shouldn't need to do it manually.

I think you're in good hands with erik_boi, who might want to confirm(or not) anything I've suggested...or better yet, might be best just to follow his advice.

---

### Post by erik_boi on 2007-01-11
> **habtish said:**
> That is handy.. I had wanted to listen to my mp3 yesterday while in the livecd and didn't want to go about installing extra codecs again.. and tried to do a ```
/media/ubuntu/usr/bin xmms 
``` which of course failed because it couldn't load some libraries. If chrooting is something that would enable me to run these apps even when they're just on a mounted drive, then it is very cool. 

Getting graphical programs to run is a little more complicated and I have never tried it but is something on my list of things to learn how to do. You could still achieve the same thing with a command line player like mplayer though. 

Could someone who is more knowledgeable about this let me know if there is any reason that the steps outlined in this debian guide [http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s-chroot]("http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s-chroot") at step 8.6.35.4 to set up multiple distributions with chroot wouldn't work in ubuntu?

> On second thought, the Ubuntu live cd probably automatically unmounts all the partitions, therefore you shouldn't need to do it manually.
I am almost certain that it does, I haven't used the ubuntu live cd except for installations in awhile. The knoppix and slax cds fulfill my needs in that department.

---

### Post by habtish on 2007-01-11
erik_boi, so happy to see you're online.. just had my first failed attempt at fixing my grub as intructed [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0")
So this is what I had done.>> As it says to run grub from the mounted linux/ubuntu partition, I mounted my ubuntu partition (hdb2) at /media/ubuntu.
```
cd /media/ubuntu/sbin
sudo ./grub
root (hd1,1)
setup (hd1,1)
``` I saw messages like found step1, step 2 and it said it reinstalled grub. Tried to reboot, same problem. So they way I took it was, since my ubuntu is on hdb2 as grub translates that as (hd1,1), that is what I should do... maybe I should set the root at the windows partition (hda2). Here is my fdisk
```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              65          68       32098+  de  Dell Utility
/dev/hda2   *          69        3686    29061585    7  HPFS/NTFS
/dev/hda3            3687        4865     9470317+   7  HPFS/NTFS
/dev/hda4               1           8       64228+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        7680    61689568+   7  HPFS/NTFS
/dev/hdb2            7681        9598    15406335   83  Linux
/dev/hdb3            9599        9729     1052257+  82  Linux swap / Solaris

```I will watch this thread for the next 20 minutes or so to see if you could spot out what I had done wrong in my initial attemp. I guess my next step would be to do
```
sudo grub
root (hd0,1)
setup (hd0,1)
```This is assuming my MBR is on the windows partition (hda2) and not on the Dell Utility partition (hda1), let me know what you think and thanks so much for your  ongoing support through this... atleast now I know it is very likely to fix this, better than yesterday when I thought I was doomed

---

### Post by habtish on 2007-01-11
taking a second look at my fdisk -l output, I see it has hdb1 flagged as bootable, which is not correct, and should be hdb2... maybe this is the problem....

---

### Post by habtish on 2007-01-11
```
grub> root (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 2,  Filesystem type unknown, partition type 0x82

grub> root (hd1,1)
 Filesystem type is ext2fs, partition type 0x83


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd1,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.


```

wish me luck...

---

### Post by habtish on 2007-01-11
so much for getting my hopes up, that didn't work. Same result when rebooting
```
 Error: 18 Selected Cylinder exceeds maximum supported by BIOS

```

---

### Post by erik_boi on 2007-01-11
after 

```
sudo grub
```

What is the output of 

```
find /boot/grub/stage1
```

like 
grub>find /boot/grub/stage1

---

### Post by habtish on 2007-01-11
> **erik_boi said:**
> after 

```
sudo grub
```What is the output of 

```
find /boot/grub/stage1
```like 
grub>find /boot/grub/stage1
this is the output
```
grub> find /boot/grub/stage1
 (hd1,1)

```

---

### Post by erik_boi on 2007-01-11
To be honest with you I am not sure why your last attempt didn't work. Maybe some else has some suggestions.

---

### Post by flyingfox on 2007-01-12
> Could someone who is more knowledgeable about this let me know if there is any reason that the steps outlined in this debian guide [http://www.debian.org/doc/manuals/re....html#s-chroot](http://www.debian.org/doc/manuals/re....html#s-chroot) at step 8.6.35.4 to set up multiple distributions with chroot wouldn't work in ubuntu?

The steps should work pretty well for Ubuntu with minor alterations if you feel like binding /dev to /foo/dev (where /foo is the root directory for your chroot) instead of using MAKEDEV. I generally just mount the /proc and /dev filesystems in my chroot with the commands "mount -t proc none /foo/proc" and "mount -o bind /dev /foo/dev". Then, I bind in any other filesystems I might need in the chroot, copy in any critical /etc files like resolv.conf or hosts.conf, and off I go with "chroot /foo /bin/bash".

To run graphical programs in a chroot you have to jump through a few more hoops after setting up a regular chroot. Basically, you have to follow these steps.

1. Make sure you are using /tmp from outside the chroot by binding it with the command "mount -o bind /tmp /foo/tmp".
2. You must use mount -o bind /dev/pts /foo/dev/pts since /dev/pts is a separate filesystem to /dev.
3. You have to copy your ~/.xauth file to the home of your user in the chroot with ```
cp /home/user/.Xauthority /foo/home/chroot_user/
``` This needs to be done everytime you restart X.

4. Finally, you must set the DISPLAY environment variable inside your chroot. Most distributions and login managers seem to use DISPLAY=":0.0" so you can set the environment variable inside your chroot with the command ```
export DISPLAY=":0.0"
```


Now, let's tackle this grub error.
> This is assuming my MBR is on the windows partition (hda2) and not on the Dell Utility partition (hda1)

The MBR is in neither partition as it generally refers to the boot sector which is located at the beginning of most storage devices. Check out the [Wikipedia article]("http://en.wikipedia.org/wiki/Master_boot_record") for details.

It would appear that /dev/hda4 is the closest you have to a "regular" boot partition as it is small and located at the beginning of your first drive in terms of cylinders. (On a sidenote, you don't seem to be using cylinders 9-64 on /dev/hda.) However, /dev/hda4 isn't flagged as bootable so it currently won't work as a /boot partition.

As confused57 pointed out earlier, it appears that you don't have a separate /boot partition so /boot is probably in your main linux partition at (hd1,1) or /dev/hdb2. However, this is not marked marked bootable so this may be the reason that grub is complaining.

In my opinion, the best way to solve this problem and prevent similar ones in the future is to use a dedicated /boot partition. As I noted earlier, /dev/hda4 is perfectly suited for this task as it is at the beginning of the drive and is relatively small. You could even incorporate the unused cylinders 9-64 into /dev/hda4 if you wanted it a little bigger, but that isn't necessary.

If you are interested in trying my solution here are the steps you should take in some livecd environment. Before making /dev/hda4 into your /boot partition, check to see what is on it and backup anything important.

1. Then mark the partition bootable in fdisk, cfdisk, or some other partitioning program. (This would also be the time to incorporate cylinders 9-64 into it.)
2. Use mke2fs /dev/hda4 to put an ext2 filesystem on the partition.
3. Copy over your files from the /boot directory in your main Ubuntu install to the new /boot partition.
4. Make sure your /etc/fstab has an entry for the /boot partition. The entry should look something like ```
/dev/hda4   /boot   ext2   noauto,noatime   1 2
``` That way your /boot partition shouldn't remain mounted after Ubuntu loads.

5. Enter the grub utility and do a "root (hd0,3)" and "setup (hd0)".

After rebooting, grub should work fine if your BIOS is set to load the MBR from the first drive or /dev/hda before the second drive.

---

### Post by habtish on 2007-01-12
Thanks flyingfox, will try these once I get home...everything makes sense so far and am not just sure with incorporating cylinders 9-64 with /dev/hda4, since I've done such things in fdisk before....

Why couldn't you stay an extra Semester huh?? You just had to ruin everything didn't ya :)

Will Post after I try your solution and hopefully will be using my Ubuntu by then. [feel free to tackle my PS/2 port problem as well... the Serial port was a joke ]

---

### Post by habtish on 2007-01-12
> 
It would appear that /dev/hda4 is the closest you have to a "regular" boot partition as it is small and located at the beginning of your first drive in terms of cylinders. (On a sidenote, you don't seem to be using cylinders 9-64 on /dev/hda.) However, /dev/hda4 isn't flagged as bootable so it currently won't work as a /boot partition.
I mounted this partition (/dev/hda4) to see what files if any I needed to backup form it.. and it does look like a boot partition.
```

ubuntu@ubuntu:/media/hda4$ ls
abi-2.6.17-10-386     initrd.img-2.6.17-10-386  System.map-2.6.17-10-386
config-2.6.17-10-386  lost+found                vmlinuz-2.6.17-10-386
grub                  memtest86+.bin

```Looking at the highest hierarchy through nautilus, (please see screenshot), it is listed as as /boot partition. This was before I mounted it at /media/hda4

So, would I still need to make that partition table or just assume all is well and flag it bootable?

---

### Post by flyingfox on 2007-01-13
> So, would I still need to make that partition table or just assume all is well and flag it bootable?

Everything appears alright so you could flag the partition bootable and then do steps 4 and 5 in my previous post.

---

### Post by habtish on 2007-01-14
> **flyingfox said:**
> Everything appears alright so you could flag the partition bootable and then do steps 4 and 5 in my previous post.

Alright, so I flagged /dev/hda4 bootable and  went into the grub utility```
root (hd0,3)
setup (hd0)
```tried rebooting and GRUB does not even load, nothing happens. Below is the current output of fdisk -l followed by my fstab entry```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              65          68       32098+  de  Dell Utility
/dev/hda2              69        3686    29061585    7  HPFS/NTFS
/dev/hda3            3687        4865     9470317+   7  HPFS/NTFS
/dev/hda4   *           1           8       64228+  83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7680    61689568+   7  HPFS/NTFS
/dev/hdb2   *        7681        9598    15406335   83  Linux
/dev/hdb3            9599        9729     1052257+  82  Linux swap / Solaris


``````
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2
UUID=03f1f827-6338-42e4-9224-b1ebdf86f4eb /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2        /media/windows    ntfs-3g       defaults,locale=en_US.utf8    0    0
/dev/hda3        /media/hda3      ntfs-3g    defaults,locale=en_US.utf8    0    0
#
/dev/hdb1        /media/hdb1      ntfs-3g    defaults,locale=en_US.utf8    0    0
#/dev/hdb3
UUID=22597278-bfcc-4519-bf61-872d002be6d5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#
/dev/hda4   /boot   ext2   noauto,noatime   1 2

```Where did I mess up flyingfox?

---

### Post by flyingfox on 2007-01-14
First off, are you able to check in your BIOS config what harddrive boots first or are your keyboard troubles still not allowing you to do so?

If you can, check to make sure your first harddrive boots first. Otherwise, you can put grub in the MBR of your second disk as well with "setup (hd1)" in the grub prompt after using the "root (hd0,3)" command. 

Also, can you check what your menu.lst file includes on /dev/hda4? Maybe files are corrupted.

---

