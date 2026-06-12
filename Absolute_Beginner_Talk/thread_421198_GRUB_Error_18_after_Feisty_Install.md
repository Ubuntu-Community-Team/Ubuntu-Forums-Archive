---
title: "GRUB Error 18 after Feisty Install"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by nwr222 on 2007-04-24
I have been using 6.10 dual boot with XP for a few months.
I tried to install 7.04 onto an unallocated section of disk and now I get GRUB Error 18 trying to boot (using the LiveCD to post this).

I had (have?) 6.10 installed onto multiple partitions spread across two disks.  My original /boot was on /hdd1 and the free space was on /hdb11.  I selected to do a simple install this time and just give it all of the free space that was available.  I am wondering if it has tried to install GRUB onto /hdb.  (I also have a disk with just XP that mounts as /hda).

If I run GParted everything looks OK, but I have noticed that the devices are being reported as /sda, /sdb. /sdc even though they are IDE drives?

Do I need to be more specific and point the /boot partition to the one that I set up first time around?

---

### Post by dannyboy79 on 2007-04-24
ok, from the live cd, type in

sudo grub

this will get you into grub's command line program. now type this in and tell what it returns.

find /boot/grub/stage1

or

find /boot/grub/stage2

or

find /grub/stage1

or

find /grub/stage2

did you previously have grub installed into hda's mbr which would point to your grub config files located in hdd1? you should've told grub to install to hdb11. then added an entry to your hdd1 menu.lst to point to the config files within hdb11 and you would have been alright. so tell me what you find with the above commands. we just need to reinstall grub and or make it point to whereever your edgy's menu.lst is.

---

### Post by nwr222 on 2007-04-24
grub> find /boot/grub/stage1
 (hd1,10)
grub> find /boot/grub/stage2
 (hd1,10)
grub> find /grub/stage1
 (hd2,0)
grub> find /grub/stage2
 (hd2,0)

I don't know where grub installed when I installed Edgy.  Apart from getting carried away with installing in lots of partitions, I don't remember specifying anything else.

---

### Post by dannyboy79 on 2007-04-25
Error 18: Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB on others.). In more practical terms this means the BIOS is unable to start executing the kernel because the kernel is not located within the block it can access at boot up time. 

I am not sure what you have done but we can fix it!!

Have you tried to change anything in the bios about which drive you bootup??? You shouldn't have, if you did, change it back and boot to the same drive as before. What's happening is that somehow a partition outside of the 8gb limit for newer drives and 512mb for the older drives is where grub is looking for stage 1 and stage 2.

We can just make this simplier than it has to be (forget about troubleshooting, it gets very time consuming and messy) by just reinstalling grub into the Master Boot Record of that drive and during that step, we need to tell grub where it can find stage 1 and stage 2 for your Edgy Install again. Then after we can at least boot to edgy and windows, I'll show you what to do to get into Fesity. 

So do that this what I want you to do.

Boot up live cd

from cli, type in 

sudo grub

root (hd2,0)

setup (hd2)

exit

This should allow you to get back to the original menu from your edgy install. let me know.

---

### Post by nwr222 on 2007-04-26
grub> root (hd2,0)

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd2)"...  15 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd2) (hd2)1+15 p (hd2,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

The commands worked, but unfortunately the result is the same.

---

### Post by dannyboy79 on 2007-04-26
ok, just show me the results of the following stuff thru the live cd.

sudo fdisk -l

(NOTE: please don't forget to "add" in exactly what the different drives/partitions contain ie:

Disk /dev/hda: 20.4 GB, 20416757760 bytes
16 heads, 63 sectors/track, 39560 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 38567 19437736+ 83 Linux **[contains ubuntu]**
/dev/hda2 38568 39560 500472 f W95 Ext'd (LBA) **[don't need to tell what this is!]**
/dev/hda5 38568 39560 500440+ 82 Linux swap **[don't need to tell me what this is either!]**

Then also show me the results of (showing me the menu.lst that Edgy is using NOT Fesity) The way that you would accomplish this is by booting to any live cd and mounting the hard drive/partition to a folder you create either within /mnt or /media so instread of cat /boot/grub/menu.lst it'll be where ever you mounted it plus this, ie cat /media/hdd4/boot/grub/menu.lst OR /mnt/hdd4/grub/menu.lst [this will be the case especially since you're using a boot partition. I do the same and sometimes it get's weird trying to figure these grub issues out when you have a boot partition.]

cat /boot/grub/menu.lst

df -h

---

### Post by nwr222 on 2007-04-27
I am not sure why these are showing as sd* - they are ide drives and my understanding is that they should show as hd*.  Previous reports show them as hda, hdb and hdd (on the second IDE bus).  Don't know if this is important.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)    **[Windows XP]**
/dev/sda2            2551        9729    57665317+   f  W95 Ext'd (LBA)   
/dev/sda5            2551        9729    57665286    b  W95 FAT32           **[Windows data]**

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)     
/dev/sdb5               2       11475    92164873+   7  HPFS/NTFS        **[Windows data]**
/dev/sdb6           11476       16556    40813101    7  HPFS/NTFS      **[Windows data]**
/dev/sdb7           16557       19106    20482843+  83  Linux            **[Edgy /home]**
/dev/sdb8           19107       19755     5213061   83  Linux              **[Edgy /usr]**
/dev/sdb9           19756       20025     2168743+  83  Linux             **[Edgy /var]**
/dev/sdb10          30141       30401     2096451   82  Linux swap / Solaris
/dev/sdb11          20026       24888    39062016   83  Linux             **[Feisty /]**

Partition table entries are not in disk order

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          13      104391   83  Linux                      **[Edgy /boot]**
/dev/sdc2              14         173     1285200   82  Linux swap / Solaris
/dev/sdc3             174         864     5550457+  83  Linux                  **[Edgy / ]**
/dev/sdc4             865        7475    53102857+   f  W95 Ext'd (LBA)
/dev/sdc5             865        5091    33953346    b  W95 FAT32           **[Windows Data]**
/dev/sdc6            5092        7475    19149448+   b  W95 FAT32         **[Windows Data]**

---

### Post by nwr222 on 2007-04-27
ubuntu@ubuntu:/media$ sudo mount /dev/sdc1 /media/EdgyBoot
ubuntu@ubuntu:/media$ ls
EdgyBoot
ubuntu@ubuntu:/media$ cd EdgyBoot
ubuntu@ubuntu:/media/EdgyBoot$ ls
abi-2.6.17-10-generic         lost+found
config-2.6.17-10-generic      memtest86+.bin
grub                          System.map-2.6.17-10-generic
initrd.img-2.6.17-10-generic  vmlinuz-2.6.17-10-generic
ubuntu@ubuntu:/media/EdgyBoot$ cd grub
ubuntu@ubuntu:/media/EdgyBoot/grub$ ls
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
ubuntu@ubuntu:/media/EdgyBoot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
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
default         4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=cf949ab3-0f34-4694-b38a-c879989c85ae ro
# kopt_2_6=root=/dev/hdd3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:/media/EdgyBoot/grub$

---

### Post by dannyboy79 on 2007-04-27
ok, I am not sure how to handle this. Are you booting into the Feisty Live CD? I am going to guess that you are since your drives are showing up as sda etc etc from fdisk -l. THis is one of the changes they made in Feisty which is causing this issue. The way grub works DIDN'T change, so drive sdc1 is hd2,0 within grub which is your boot partition. You told me before that it was hdd1, which is actually hd3,0 within grub. THis is most likely the problem. according to what I am seeing your root filesystem is located on the 3rd hard drive, 3rd partition of that drive and your grub root device is located within the 3rd hard drive on the 1st partition of that drive. you need to change your Edgy menu.lst, see below:\

FROM THIS:
# kopt_2_6=root=/dev/hdd3 ro

TO THIS:
# kopt_2_6=root=/dev/**hdc3** ro

Also, all your kernel lines are  wrong as well, according to your fdisk, all your kernel lines are currently looking for the kernels within tha same place when you don't even have an hdd drive (which is the 4th hard drive)


***_WAIT_***, i just thought of something, is your cdrom or dvdrom on IDE channel 0 which would make it hda??? If so, then your 3rd hard drive hdc1 will turn into hdd1 which is what you have in your menu.lst. HUH??? Now I am stumped for sure. I need to see a couple of your Edgy files.

/boot/grub/device.map

Also please inform me of everything within your system, optical drives, all hard drives etc etc. Show me this output from this command also

dmesg | grep CD

AND

dmesg | grep DVD

We'll have to go from there.

---

### Post by confused57 on 2007-04-27
dannyboy79,  you definitely have everything under control...but I was wondering if he could just install his Edgy grub back to his (hd0) drive, i.e.

root (hd2,0)
setup (hd0)

in order to get his system to boot again.

Feisty definitely has a different way of designating drives...my hda drive is sda in Feisty, and my sda drive is sdb, go figure.

---

### Post by psusi on 2007-04-27
You want sdc3 not hdc3, since there is no hdc, and yea, root (hd2,0) setup (hd0) should do the trick, provided that the bios is configured to boot from the windows drive.

---

### Post by dannyboy79 on 2007-04-27
> **confused57 said:**
>  dannyboy79,  you definitely have everything under control...but I was wondering if he could just install his Edgy grub back to his (hd0) drive, i.e.

root (hd2,0)
setup (hd0)

in order to get his system to boot again.

Feisty definitely has a different way of designating drives...my hda drive is sda in Feisty, and my sda drive is sdb, go figure. 

DAH, you're right. I thought I asked him which hard drive he was booting from his bios and I thought it was his edgy install (this was before he posted him fdisk) BUT now that I see his fdisk output and now that you have jogged my memory, I gave him the grub install command to install grub into the mbr of his edgy harddrive and that's probably not the one he is booting to. 

So the question is, what hard drive are you booting from the bios???? If it is the windows system hard drive (sda), THEN

Solution will be what confused57 stated.

root (hd2,0)
setup (hd0)

BUT if you're booting to any other drive let me know which one and we'll go from there.


[QUOTE=psusi]You want sdc3 not hdc3, since there is no hdc, and yea, root (hd2,0) setup (hd0) should do the trick, provided that the bios is configured to boot from the windows drive.[/QUOTE]
THAT IS NOT CORRECT. There does exist a hdc drive, IN EDGY. Myself and the thread originator are going to be booting into edgy's install and then we're going to point edgy's menu.lst to a config file which will then boot up feisty. The reason for doing this is due to kernel updates, this way edgy's kernel and AUTO update when he is working in Edgy and the same goes for when he'd be working in Feisty, AUTO update will work and update both his menu.lst files located within their respective folders.

---

### Post by psusi on 2007-04-27
You will not be able to have update-grub work properly from both an edgy and a feisty install.  The devices.map will either point to hdc or to sdc, so one system will work and the other will not.  I also assumed that he was planning on installing grub from the same environment he produced the fdisk -l on, and in that case, he will need to use sdc.

---

### Post by nwr222 on 2007-04-27
Thanks everyone - I can now boot XP and my old Edgy, as you can see below, and I know a bit more about GRUB and devices than I did before I started (which was not hard).

Assumptions were corrrect I am booting from the 1st drive on the 1st IDE (was /hda).  The first drive on the second IDE is my DVD (was /hdc under Edgy). 

nrees@nrees-desktop:/boot/grub$ cat device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/hdd

Can I explain what I was attempting and perhaps there is a better way.
- My Edgy was installed into too many partitions, but it took me a while to get it going so I don't want to loose it
- I wanted to try Feisty,  I thought I was taking a safe path doing another install rather than an upgrade
- I installed Feisty into one new partition, assuming that it would be sensitive to the existing XP and Edgy installs
- My plan was to try Feisty, and once I was happy it was working, then I could remove the Edgy install completely (not sure how I planned to do this.  Had not thought that far ahead).

I am happy to reinstall Feisty if there is a better way to get the same result.

---

### Post by confused57 on 2007-04-27
Glad you were able to get Windows & Edgy booting again...dannyboy79's not online right now, but think I know what he was planning on suggesting.  Boot into Edgy, open your /boot/grub/menu.lst & add an entry to boot Feisty at the very end of the file, using configfile:

```
title   Feisty
savedefault
configfile  (hd1,10)/boot/grub/menu.lst
```

you can try this until he gets back online.

---

### Post by nwr222 on 2007-04-27
Interesting.  With the addidtions to the menu, I end up with the same problem - Error 18.

Is the placement of my Fiesty partition too far through the disk.  This is a very old PC, and the Fiesty partition is on a large disk behind some big windows partitions.  I am wondering if I should rearrange everything and do this closer to the start of the disk.

What I don't understand is with your proposed addition to the menu.lst, I get the change to the menu, so it has got as far a reading the menu.lst, but all options give Error 18, not just the new entry for Feisty.

---

### Post by confused57 on 2007-04-27
> **nwr222 said:**
> Interesting.  With the addidtions to the menu, I end up with the same problem - Error 18.

Is the placement of my Fiesty partition too far through the disk.  This is a very old PC, and the Fiesty partition is on a large disk behind some big windows partitions.  I am wondering if I should rearrange everything and do this closer to the start of the disk.

What I don't understand is with your proposed addition to the menu.lst, I get the change to the menu, so it has got as far a reading the menu.lst, but all options give Error 18, not just the new entry for Feisty.

Just adding the entry to boot Feisty shouldn't affect your ability to boot your other OS's, unless trying to boot Feisty changed something in your configuration.  What you can try is to reinstall Edgy's grub(again):
root (hd2,0)
setup (hd0)

then try to boot into Edgy(not Feisty), if you can, then remove the Feisty entry from your Edgy menu.lst

You could still reinstall Feisty on the same partition that you have it, but if you can, maybe set up a small boot partition at the beginning of the hard drive...don't try to use the same boot partition that you're using for Edgy, because I believe Feisty will overwrite configuration files with the same name & you wouldn't be able to boot Edgy.  dannyboy79 will be able to advise you on what would be your best course of action.

Added:  Here's a link describing grub error 18 & some other possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by nwr222 on 2007-04-30
I am stumped again.  I have done the following.  Starting with a working dual boot XP/Edgy system using the help above

1 - Freed up some space at the start of /hdb aka /sdb
2 - created small boot partition and root partition for Feisty
3 - Installed Fiesty again on the new boot, root and the old home
4 - reboot => back to Error 18 ??
5 - checked out the new boot partition - the menu.lst looks good (has entries for XP and Edgy)
6 - Reinstalled grub using root (hd1,0), setup (hd0) - details follow
7 - reboot => still Error 18
8 - Reinstalled grub using (hd2,0), setup (hd0)
9 - Back to a dual boot XP/Edgy 

**Details**
Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/hdb5            2641       11475    70967137+   7  HPFS/NTFS
/dev/hdb6           11476       16556    40813101    7  HPFS/NTFS
/dev/hdb7           16557       19106    20482843+  83  Linux
/dev/hdb8           19107       19755     5213061   83  Linux
/dev/hdb9           19756       20025     2168743+  83  Linux
/dev/hdb10          30141       30401     2096451   82  Linux swap / Solaris
/dev/hdb11          20026       24888    39062016   83  Linux
/dev/hdb12              2          17      128457   83  Linux              **[New boot partition]**
/dev/hdb13             18        2640    21069216   83  Linux         **[New root partition]**

nrees@nrees-desktop:/media$ sudo mount /dev/hdb12 fboot
nrees@nrees-desktop:/media$ sudo mount /dev/hdb13 froot
nrees@nrees-desktop:/media$ cd fboot
**nrees@nrees-desktop :/media/fboot$ ls**
abi-2.6.20-15-generic             lost+found
config-2.6.20-15-generic          memtest86+.bin
grub                              System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic      vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak
[B]nrees@nrees-desktop:/media/fboot$ cd grub
nrees@nrees-desktop:/media/fboot/grub$ ls[/B]
default        fat_stage1_5       menu.lst           stage1
device.map      installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5
**nrees@nrees-desktop:/media/fboot/grub$ cat device.map**
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc 

**nrees@nrees-desktop:/media/fboot/grub$ cat menu.lst**
....
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,11)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=0af8b2c2-9439-4d6d-ac2d-eb400a9348fa ro quiet splash
initrd          /initrd.img- 2.6.20-15-generic
quiet
savedefault
....
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
....
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sdc3)
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash
initrd          /initrd.img- 2.6.17-10-generic
savedefault
boot

**Run grub setup (again)**
grub> root (hd1,11)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 d (hd0) (hd0)1+17 p (hd1,11)/grub/stage2 /grub/m
enu.lst"... succeeded
Done.

---

### Post by dannyboy79 on 2007-04-30
> **psusi said:**
> You will not be able to have update-grub work properly from both an edgy and a feisty install.  The devices.map will either point to hdc or to sdc, so one system will work and the other will not.  I also assumed that he was planning on installing grub from the same environment he produced the fdisk -l on, and in that case, he will need to use sdc.

Wrong again!!!! Please don't make comments about things that you don't understand how they work. I've already explained how I am helping him set it up and if you still don't understand I am sorry but I can't explain explain it again.

grub-update will work for both of his installs as they both use different device.map files and that's all I have to say about that.

---

### Post by dannyboy79 on 2007-04-30
> **nwr222 said:**
> I am stumped again.  I have done the following.  Starting with a working dual boot XP/Edgy system using the help above

1 - Freed up some space at the start of /hdb aka /sdb
2 - created small boot partition and root partition for Feisty
3 - Installed Fiesty again on the new boot, root and the old home
4 - reboot => back to Error 18 ??
5 - checked out the new boot partition - the menu.lst looks good (has entries for XP and Edgy)
6 - Reinstalled grub using root (hd1,0), setup (hd0) - details follow
7 - reboot => still Error 18
8 - Reinstalled grub using (hd2,0), setup (hd0)
9 - Back to a dual boot XP/Edgy 

**Details**
Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/hdb5            2641       11475    70967137+   7  HPFS/NTFS
/dev/hdb6           11476       16556    40813101    7  HPFS/NTFS
/dev/hdb7           16557       19106    20482843+  83  Linux
/dev/hdb8           19107       19755     5213061   83  Linux
/dev/hdb9           19756       20025     2168743+  83  Linux
/dev/hdb10          30141       30401     2096451   82  Linux swap / Solaris
/dev/hdb11          20026       24888    39062016   83  Linux
/dev/hdb12              2          17      128457   83  Linux              **[New boot partition]**
/dev/hdb13             18        2640    21069216   83  Linux         **[New root partition]**

nrees@nrees-desktop:/media$ sudo mount /dev/hdb12 fboot
nrees@nrees-desktop:/media$ sudo mount /dev/hdb13 froot
nrees@nrees-desktop:/media$ cd fboot
**nrees@nrees-desktop :/media/fboot$ ls**
abi-2.6.20-15-generic             lost+found
config-2.6.20-15-generic          memtest86+.bin
grub                              System.map-2.6.20-15-generic
initrd.img-2.6.20-15-generic      vmlinuz-2.6.20-15-generic
initrd.img-2.6.20-15-generic.bak
[B]nrees@nrees-desktop:/media/fboot$ cd grub
nrees@nrees-desktop:/media/fboot/grub$ ls[/B]
default        fat_stage1_5       menu.lst           stage1
device.map      installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5
**nrees@nrees-desktop:/media/fboot/grub$ cat device.map**
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc 

**nrees@nrees-desktop:/media/fboot/grub$ cat menu.lst**
....
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,11)
kernel          /vmlinuz-2.6.20-15-generic root=UUID=0af8b2c2-9439-4d6d-ac2d-eb400a9348fa ro quiet splash
initrd          /initrd.img- 2.6.20-15-generic
quiet
savedefault
....
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows NT/2000/XP
root            (hd0,0)
savedefault
makeactive
chainloader     +1
....
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sdc3)
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash
initrd          /initrd.img- 2.6.17-10-generic
savedefault
boot

**Run grub setup (again)**
grub> root (hd1,11)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /grub/stage1 d (hd0) (hd0)1+17 p (hd1,11)/grub/stage2 /grub/m
enu.lst"... succeeded
Done.

You're still creating Feisty's boot partition to far. It has to be within the first 8 gb since your computer is old. Have you tried to flash the bios with an updated bios? My suggestion is to leave the root of feisty where it is but move the boot partition to within the 8gb.


Also, due to Feisty useing sdX instead of hdX, you can't boot edgy directly from feisty and the same goes the otherway, you'll need to boot using the config option like confused stated which is what I was planning on helping you with. I am glad he stepped in and got your Edgy and WinXP to boot. 

There may be a way to use all UUID's but I am not sure if that'll work either since the device.map isn't useing UUID's. You could change your fstab to use UUID's and you could even change you grub boot lines to use UUID's but I am not sure if grub can read the device.map if it had (hd1) = UUID=blah blah.

So do as I suggest per above, create a boot partition within the first 8gb that's about 1gb in size and you should be fine doing exactly what Confussed suggested with booting into Edgy FIRST, then adding the boot to configfile suggestion to get to Feisty. Good luck, you're almost there.

I always strongly suggest backing up all data on drives that you're moving and resizing partitions just as a fail safe. Either use tar.gz for ntfs to backup adt the file level, and use partimage to backup ext3 at the filesystem level

---

### Post by psusi on 2007-04-30
> **dannyboy79 said:**
> 
grub-update will work for both of his installs as they both use different device.map files and that's all I have to say about that.

Sure, but how are you going to get the two installs to use two different device.maps, yet still share a single /boot?

nwr:  your partition layout on that drive is really strange.. you have no primary partitions and a crapload of extended partitions.  If this old pc can't see past 8 gb, then /boot needs to be entirely under the 8 gb mark, and it needs to be a primary partition.

Another thing you can try is adding the --force-lba option to the grub setup command.  Your bios might be capable of booting past 8 gb, but grub might not think it can so it doesn't try.  It is rare, but it did happen sometimes on older machines.

---

### Post by dannyboy79 on 2007-04-30
well that's a great point. I had already mentioned earlier that he would need to leave his boot partition alone for Edgy and make a new boot partition earlier in the disk. this will allow both grub-updates to work. there's no way to combine them with feisty device.maps being so different than edgy's in relation the sdX versus hdX.

i believe that grub can be booted from an extended partition as long as it's within the first 8 gb. so he's basically going to have to resize his very first partition hdb5 and leave about 1gb in front of it. I would actually just suggest redoing eveything by backing everything up and putting back into place once you recreate all your partitions utilizing 3 primary's and 1 extended and then all of hte rest that you need.  I always strongly suggest backing up all data on drives that you're moving and resizing partitions just as a fail safe. Either use tar.gz for ntfs to backup adt the file level, and use partimage to backup ext3 at the filesystem level.

i can walk you thru the backing up process and the extraction back onto the clean partitions etc etc. it'd be almost safest to use windows to create the ntfs partition as I have already tried to use gparted and when I tried to boot windows xp into it, I got a disk read failure. I even used recovery console to do a full automatica repair which is suppose to fix the mbr, do a fixboot and all that but to no avail. that was using Partimage and Gparted for a winxp install. this was a test that I jsut did recently. It was a fresh install too, with no fragmentation. so i used partimage to backup to a usb fat32 drive, then i used to gparted to delete partitions, and recreate them, then I used partiamge to place the partition image back, everything seemed fine up until I tried to boot, no go, even after trying to repair it all and everything. i couldn;'t even get grub to chainload it so you may want to use Ghost or Arconis for NTFS partition creation and or backing up at the partition level.

---

### Post by nwr222 on 2007-04-30
*he would need to leave his boot partition alone for Edgy*

I have left the edgy alone, and I am comfortable that I can get back to it
[I]
make a new boot partition earlier in the disk[/I]

The partitions that I am using now for Feisty are
boot = /dev/hdb12
root = /dev/hdb13

From  the following you will see that

/dev/hdb12 goes from 2 to 17
/dev/hdb13 goes from 18 to 2640
/dev/hdb5 goes from 2641 up

The numbering is from the order they were created, not the position on the disk.

_I already did exactly what you describe_
1 - shrunk /dev/hdb5 (I shrunk it to give myself 20G spare)
2 - moved it up to free up some space at the front of the drive (don't worry all my data is backed up)
3 - created two new partitions as above
4 - Reinstalled Feisty

Device Boot Start End Blocks Id System
/dev/hdb1 2 30401 244188000 f W95 Ext'd (LBA)
/dev/hdb5 2641 11475 70967137+ 7 HPFS/NTFS
/dev/hdb6 11476 16556 40813101 7 HPFS/NTFS
/dev/hdb7 16557 19106 20482843+ 83 Linux
/dev/hdb8 19107 19755 5213061 83 Linux
/dev/hdb9 19756 20025 2168743+ 83 Linux
/dev/hdb10 30141 30401 2096451 82 Linux swap / Solaris
/dev/hdb11 20026 24888 39062016 83 Linux
[B]/dev/hdb12 2 17 128457 83 Linux [New boot partition]
/dev/hdb13 18 2640 21069216 83 Linux [New root partition][/B]

---

### Post by louieb on 2007-04-30
> **nwr222 said:**
> Do I need to be more specific and point the /boot partition to the one that I set up first time around?
Thats the normal cure for grub error 18  
[Gentoo Linux Grub Error Collection]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by psusi on 2007-04-30
The problem is that extended partitions are chained.  To find partition 13, you have to look at partition 1, then 5, then 6, then 7, 8, and so on before reaching 13.  Because a partition in that chain is above 8 gb, it can not be found.  This is why I said to make the /boot partition(s) primary partitions.  

If I were you I would just stick with a single /boot partition, and make sure that only one system ever runs update-grub.  That will be easier than trying to maintain two different and complex menu.lsts capable of booting both systems.

---

### Post by nwr222 on 2007-05-01
Thanks everyone - I have a successful outcome

I reorganised my /sdb disk so that the two new partitions at the front of the disk are primary, not extended.  This was pretty easy using GParted.

I reinstalled Fiesty.  As I observed earlier, the Feisty install recognsed all of my OS installs and built them into the menu.lst - and this time the new feisty boots.  So now I have XP / Edgy / mynewFeisty / myfirstFeisty all in the menu!  The grub install has worked and points at my new /boot.   My first Feisty, which was installed on a trailing partition, still returns Error 18, but all of the others boot OK.

/dev/sdb1            2640       30401   222998265    f  W95 Ext'd (LBA)
/dev/sdb2               1          25      200781   83  Linux          ** [New Boot]**
/dev/sdb3              26        2639    20996955   83  Linux   ** [New Root]**
/dev/sdb5            2641       11475    70967137+   7  HPFS/NTFS

---

### Post by dannyboy79 on 2007-05-01
so are you still using 2 different boot partitions, one for edgy and one for feisty? and your boot line for feisty in your menu.lst boots a config file right? if so than that is exactly what I was trying to accomplish and I so glad that you got it. great job sticking with it. glad I could be of help.

---

### Post by nwr222 on 2007-05-02
Yes, I am still using two boot partitions.  My Edgy install is untouched.  Once I installed Feisty into a new boot at the start of the disk, the install process took care of the rest.  It created the following entry in the menu.lst to boot the old Edgy install.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sdc3)
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash 
initrd          /initrd.img-2.6.17-10-generic
savedefault
boot

Thanks again for your help.

---

### Post by dannyboy79 on 2007-05-02
> **nwr222 said:**
> Yes, I am still using two boot partitions.  My Edgy install is untouched.  Once I installed Feisty into a new boot at the start of the disk, the install process took care of the rest.  It created the following entry in the menu.lst to boot the old Edgy install.

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdc3.
title           Ubuntu, kernel 2.6.17-10-generic (on /dev/sdc3)
root            (hd2,0)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hdd3 ro quiet splash 
initrd          /initrd.img-2.6.17-10-generic
savedefault
boot

Thanks again for your help.

Ok, well this is not what you want, your edgy kernel will NOT get auto-updated when it downloaded a new kernel image therefore once you shutdown and try to restart, you won't be able to boot into Edgy, well you will but it won't be using the new kernel. That's why the instructions were to install Grub which would "see" edgy's stage 1.5 and stage 2 files, then within that, there would be a menu pick for Feisty which would then bring you to Feisty's grub menu. this way, which ever ubuntu you boot into and get a kernel update thru, grub will be auto-updated and use the new kernel AUTOMAGICALLY. but that's not what you did. 

What has happend is that you chose to install grub during the Feisty Install (or maybe it occured without asking you) and now when grub loads,  the menu that appears is because grub located the stage 1.5 and stage 2 for your feisty install and is showing you your Feisty menu.lst which at the way bottom as your showing me, is where you Edgy boot lines are. 

Hey it's working and I can understand if you don't want to futz with it but this is definitely not the way I would have done it.

---

### Post by nwr222 on 2007-05-03
I achieved my original objective, and I did learn something about grub and partitions.  Ultimately I plan to blow away the Edgy completely, once I am comfortable everything is working in Feisty.

I would still be happy to continue to get this implemented following your original plan, if you have the patience to guide me through.  I am at the limits of my understanding at this point - I don't fully understand the end state.  I think that I at least start with OSs that definitely boot.  If you want to continue can you recap the steps for me.

Q: If it will work with grub seeing the 1.5 & 2 Edgy and then allow me to boot Fiesty from there - will this also work the other way around?  I.e. start with the Feisty and set it up to boot Edgy?

---

### Post by dannyboy79 on 2007-05-03
> **nwr222 said:**
> I achieved my original objective, and I did learn something about grub and partitions.  Ultimately I plan to blow away the Edgy completely, once I am comfortable everything is working in Feisty.

I would still be happy to continue to get this implemented following your original plan, if you have the patience to guide me through.  I am at the limits of my understanding at this point - I don't fully understand the end state.  I think that I at least start with OSs that definitely boot.  If you want to continue can you recap the steps for me.

Q: If it will work with grub seeing the 1.5 & 2 Edgy and then allow me to boot Fiesty from there - will this also work the other way around?  I.e. start with the Feisty and set it up to boot Edgy?
of course it would, basically instead of directly booting the other OS's kernel using grub, we going to point grub to another grub, which from there you can chose the other OS. so this is what you do and it's very easy. Since you want to boot into Feisty's grub first we don't even have to reinstall grub, we'll use Feisty's grub menu to end up getting to Edgy's grub menu to be able to boot edgy. ONLY IF YOU DIDN'T DO ANYTHING TO EDGY'S BOOT PARTITION WILL THIS WORK. I am saying that this is the FDISK info I am assuming is still correct and the below change will only work if this is still true:
(NOTE: also, was this fdisk from Feisty which is why it states sdc or is it in fact a SATA hard drive?)

Disk /dev/sdc: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 1 13 104391 83 Linux **[Edgy /boot]**
/dev/sdc2 14 173 1285200 82 Linux swap / Solaris
/dev/sdc3 174 864 5550457+ 83 Linux **[Edgy / ]**
/dev/sdc4 865 7475 53102857+ f W95 Ext'd (LBA)
/dev/sdc5 865 5091 33953346 b W95 FAT32 [Windows Data]
/dev/sdc6 5092 7475 19149448+ b W95 FAT32 [Windows Data]

Open up your menu.lst which Feisty uses and instead of the Edgy boot lines at the very bottom, simply change ALL of it to this:

title   Edgy
savedefault
configfile  (hd2,0)/grub/menu.lst


**If that DOES NOT work, than please post back the results of these commands:**

```
sudo fdisk -l
```  (NOTE: please inform me which OS you're working in when using these command)

and also both of these command for your edgy install

```
cat /boot/grub/menu.lst
```

```
cat /boot/grub/device.map
```

and then do this and post back the results so I can verify something

```
sudo grub
```

```
find /boot/grub/stage1
```

```
find /grub/stage1
```


```
exit
```

---

### Post by nwr222 on 2007-05-04
This has worked - I think as you expect.  If I select the new menu option, I am now presented with the menu from the Edgy boot, and I can select any of the options form that menu.lst.
Very cool.  Thanks again.

---

### Post by dannyboy79 on 2007-05-04
> **nwr222 said:**
> This has worked - I think as you expect.  If I select the new menu option, I am now presented with the menu from the Edgy boot, and I can select any of the options form that menu.lst.
Very cool.  Thanks again.

i am glad to have helped. this way when you're in Edgy and you're presented with a kernel update, grub-update will AUTOMAGICALLY update your menu.lst with the new kernel boot option. and the same goes for Feisty, this is more versatile. whereas before, if you were in edgy and presented with a kernel update, i don't know what would've happen, it might have even screwed up your Feisty boot options within the menu.lst (as I said though, I don't know what would happen) ok, I am going to unsubscribe from the thread now since you're all set.

---

