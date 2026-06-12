---
title: "Config Grub to recognize windows"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2006-07-28
Hey all, I've installed ubuntu a few days ago, and have not been able (mostly because I haven't tackled it yet) to boot into windows. It is not an option in grub, it automatically loads ubuntu. I've seen various threads about editing files, but I'm still a little unsure. Below I'm including my boot/grub/menu.lst. There is no option for windows in there. My ubuntu install (/) should be on hda8, and windows on hda5 (except that should be 7 and 4 in grub, because it starts at 0, correct?). Can I just add the windows alternative into the .lst (and if so, how and where) or do I need to run a tool in order to set grub up appropriately to have the option to boot into windows? Thanks in advance for any help that you can provide.

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Paerez on 2006-07-28
you can just add it in:
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
replace hd0,0 with hd0,4 as you thought, and remove the comments.

---

### Post by smurphv2 on 2006-07-28
Thanks for the suggestion. I added the lines you said to, and when I try to boot into windows, I get the following message:

```
root(h0,4)
filesystem type unknown, partition type 0x7
make active
Error 12: Invalid device requested
Press any key to continue...
```

This then leads me back to the grub menu, where I can boot ubuntu just fine. If it helps, windows XP is on an NTFS partition, and before installing ubuntu, there were no issues with windows in terms of it booting or other errors. For consistency, I'm including the updated menu.lst

```

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
#title		Windows 95/98/NT/2000
#root		(hd0,4)
#makeactive
#chainloader	+1
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
# kopt=root=/dev/hda8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Windows 95/98/NT/2000
root		(hd0,4)
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda8 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by Paerez on 2006-07-28
that means hd0,4 is wrong. Whats your fstab say? or fdisk's output? are you sure its hda5?

---

### Post by smurphv2 on 2006-07-28
/etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb4       /media/backup   vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda2       /media/download ext3    defaults        0       2
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb2       /media/hdb2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hdb1       /media/music    ext3    defaults        0       2
/dev/hda3       /media/storage  ext3    defaults        0       2
/dev/hda6       /media/video    ext3    defaults        0       2
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2       10198    81907402+   f  W95 Ext'd (LBA)
/dev/hda2           10199       16709    52299607+  83  Linux
/dev/hda3           16710       19457    22073310   83  Linux
/dev/hda5               2        3825    30716248+   7  HPFS/NTFS
/dev/hda6            8925       10198    10233373+  83  Linux
/dev/hda7            8925        8925          30+  83  Linux
/dev/hda8            3826        8924    40957686   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2550    20482843+  83  Linux
/dev/hdb2            2551        8924    51199155    7  HPFS/NTFS
/dev/hdb3            9606        9729      996030   82  Linux swap / Solaris
/dev/hdb4            8925        9605     5470132+   b  W95 FAT32

Partition table entries are not in disk order

```

Under Places > Computer, if I click on volume "hda5" that has all of my windows folders, etc. Thank you very much for your help.

---

### Post by Paerez on 2006-07-28
> root(h0,4)
typo! you are one D away from windows.

---

### Post by smurphv2 on 2006-07-28
I'm not seeing the error. My menu.lst had the line as "root (hd0,4)" I've tried removing the d, and adding it again, but in either case, it didn't work. When I removed the d, I received a parse error, most likely due to the fact that it didn't know what (h0,4) was. However, with the "d" added, I have the "filesystem unknown" error mentioned above.

---

### Post by Paerez on 2006-07-28
oh damn and I thought I solved it. I'm not sure what it is then...

---

### Post by smurphv2 on 2006-07-28
Thanks for all your help and suggestions. Anyone else have any ideas?

---

### Post by djsroknrol on 2006-07-28
I don't know if it would make a difference, but every menu.lst I've ever seen has a separator from the Debian menu items..look at mine:

```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 acpi=off ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
boot

#[B]## END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		**********************Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

[/B]
```

Note the items in bold..even though I'm dual booting 2000Pro, it's the same...maybe you have it right (hda5), but not in the right place in the menu?..can't hurt to cut and paste mine and alter it for your OS...

---

### Post by confused57 on 2006-07-28
You could try a GAG floppy to boot Windows:
[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

Also, when your grub menu displays at startup, highlight the Windows entry, press "e", then try various combinations for the Windows root location & try to boot...if you find one that works, then you can make it permanent in your menu.lst.

---

### Post by smurphv2 on 2006-07-31
anyone else have any ideas? Thanks for all the suggestions so far, but other than the gag disk (which I haven't had any time to try yet) none of them have worked.

---

### Post by smurphv2 on 2006-08-02
I've tried a GAG boot disk, and even that hasn't worked. I'm not sure what the problem is. I can mount the partition in ubuntu, and see all the files just fine. Before installing ubuntu, I was able to boot windows with no issue. Any other drastic measures (or not so drastic) that I may take in order to maybe get my dual boot working?

---

### Post by tonyisntcreative on 2006-08-02
This could be the boot flag for the partition...I had a problem of Windows not booting on our family computer the other day and this was the problem.  I'm not sure if it is for you, but it's worth a shot.

This is what I did to fix it....

I use GParted LiveCD.  It's the same GParted you use under Linux with some slight changes.  You can also get a USB copy I now see.
[CD](http://prdownloads.sourceforge.net/gparted/gparted-livecd-0.2.5-3.iso?download) and [USB](http://prdownloads.sourceforge.net/gparted/gparted-liveusb-0.2.5-3.zip?download)

When you boot into it it starts up GParted.  Your Windows partition (in your case /dev/sda5) SHOULD have "boot" under the "flags" column.  If it doesn't, select /dev/sda5, right click, and go to "manage flags."  Then check the "boot" option.

Maybe that will help?  Good luck.

---

### Post by smurphv2 on 2006-08-02
Tony,
    Thanks for your reply. The windows partition flag was not set to "boot", so I changed it so that it was, but that still did not resolve the issue. I appreciate your suggestion though.

---

### Post by catlett on 2006-08-02
Try running it with the noverify option. This just sends the loader to the partition, it doesn't try to mount it. Sometimes it works when the regular way doesn't.
Anyways, put this entry in your grub menu.
```
sudo gedit /boot/grub/menu.lst
```
```
title           Microsoft Windows
rootnoverify            (hd0,4)
chainloader     +1
```
If this doesn't work, you can always restore your windows bootloader and then try to boot Ubuntu with gag.
You will need a windows xp installation disk to do it though. It requires booting into the recovery option and then issuinbg the command ```
fixmbr
``` at the C:\ command propmt.
If you can boot windows, use gag and hopefully it will boot you to ubuntu.

---

### Post by tonyisntcreative on 2006-08-03
At this point you can probably reinstall grub, too, but with the correct windows section in menu.lst.

---

### Post by catlett on 2006-08-03
Actually you could try re-installing grub. Grub usually recognizes windows and adds the entry automatically. It couldn't hurt.
```
sudo grub-install /dev/hda
```

---

### Post by smurphv2 on 2006-08-09
the noverify option did not yield any results. I will try tonight to run the fixmbr from the recovery option. Should I try re-installing grub (via the last post) before attempting this, or after? It seems that the problem to begin with is that grub does not recognize my windows partition. Then again, neither does GAG. All of which is very strange, because the partition is still there, mountable, has my data on it, and was bootable before installing ubuntu.

---

### Post by Tomosaur on 2006-08-09
If you use fixmbr, you will need to reinstall grub.

Before you do, have you tried 'sudo update-grub' in a terminal?

---

### Post by junglepeanut on 2006-08-09
I just thought I would add my menu if it helps I figure it can't hurt and it allows everyone to see I haven't cleaned up some old images yet. lol.

Dual booting ubuntu and XP (Of note I have not been on XP in months)
```
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
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

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
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-25-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

---

