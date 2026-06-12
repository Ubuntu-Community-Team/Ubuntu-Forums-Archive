---
title: "dual boot problems?"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by jimmp226 on 2006-01-09
I've got Ubuntu 5.10 installed in my laptop along with Windows XP. Both systems are loaded in there own partition. But when I start my computer it starts right into Ubuntu. I pressed the excape key and it showes 5 differant Ubuntu (programs?) items to pick from but no Windows. I tried to put the Windows recoverydisk in it says that Windows is in the right partition. Any ideas? Jim

---

### Post by frodon on 2006-01-10
You could try that : [http://ubuntuguide.org/#addwindowsentrygrubmenu](http://ubuntuguide.org/#addwindowsentrygrubmenu)

---

### Post by jimmp226 on 2006-01-10
Thanks for the help. Now this is what that says:

e.g. Assumed that  /dev/hda1 is the location of Windows partition

sudo cp /boot/grub/menu.1st /boot/grub/menu.1st_backup
sudo gedit /boot/grub/menu.1st


OK-   my Windows partition is in  (at?)   hda5
 What in this code would I need to change to make this work?

Sorry for the stupid question but I have no idea what I'm doing in a Linux system? Thanks in advane for all of the great ideas. Jim

---

### Post by frodon on 2006-01-10
If your windows partition is located in hda5 the lines to add in menu.list should be : ```
title		Microsoft Windows
root		(hd0,4)
savedefault
makeactive
chainloader	+1
```

---

### Post by lha on 2006-01-10
[QUOTE=jimmp226]Thanks for the help. Now this is what that says:

e.g. Assumed that  /dev/hda1 is the location of Windows partition

sudo cp /boot/grub/menu.1st /boot/grub/menu.1st_backup
sudo gedit /boot/grub/menu.1st


OK-   my Windows partition is in  (at?)   hda5
 What in this code would I need to change to make this work?

Sorry for the stupid question but I have no idea what I'm doing in a Linux system? Thanks in advane for all of the great ideas. Jim[/QUOTE]

There's nothing in those two lines you need to change. The first one makes a backup of the file you are going to edit and the second one opens it in an editor. Frodon already told the changes you need to apply to menu.lst. (Partition numbers start from 0 in grub.)

---

### Post by jimmp226 on 2006-01-10
Ok I tried that. Even think I did it right? But I'm not sure? It didn't work though. I copied each line by it's self and pasted them 1 at a time into the terminal and hit enter that brought me to the menu.lst (page?folder?). From there I went about a third of the way down the page untill I found

:
# password topsecret

#
# examples
#
# title		Microsoft Windows 
# root		(hd0,4)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST



I changed it to look  as told and no luck. I'm sure it's me but I don't know what I'm doing. Please help. lol    Jim

P.S. the above is copied from the menu.list page just part of it though.

---

### Post by frodon on 2006-01-10
Be careful the character **#** means that the line is commented, it could explain why your modification doesn't work.
So make sure you put the lines i gave you (uncommented) in the menu.list if they don't already exist (uncommented).

---

### Post by J77 on 2006-01-10
Did you create a /boot partition during the initial installation?

---

### Post by jimmp226 on 2006-01-10
Frodon thanks for the help. I found thoese lines and just changed the name and hda0,4 i didnt add the lines if that makes any scense? J77 I dont know what that is so I guess not. I paritationed my hard drive as follows:
C: Ubuntu
D: Windows XP
E: Cd Drive
F: External hard drive

I did this in Windows or that's how it's listed in Windows
In Ubuntu windows is in: hda5

Hope some of this helps and again thank you for taking your time to help. I really apperciate all the help. Jim

---

### Post by frodon on 2006-01-10
Could you attach your menu.lst file in the next post ? 
it would be easier to see if you made something wrong with the whole file.

---

### Post by jimmp226 on 2006-01-10
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
# title		Microsoft Windows 
# root		(hd0,4)
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
# kopt=root=/dev/hda6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Microsoft Windows
root		(hd0,4)
savedefault
makeactive
chainloader	+1



title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Irony on 2006-01-10
Note do this first (don't confuse l with 1 (copy and paste));

[PHP]sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
[/PHP]

Menu should be like this (copy and paste) - note timeout I've put as 20 so you can see the options (note Windows is usually on (hd0,0), have you got the correct partition);

[PHP]# menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		20

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows
root		(hd0,4)
savedefault
makeactive
chainloader	+1[/PHP]

If it doesn't work and you end up in terminal on boot up do;

[PHP]sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst
reboot
[/PHP]

Note post a *sudo fdisk -l* readout prior to this to see what your partitions are if you don't know.

---

### Post by jimmp226 on 2006-01-10
Thanks Irony. That did some thing? Now when I restart my computer I get a screen that showes Microsoft Windows as another operating system so thats good. But when I click on it it says something about the partition not being there . If I go to system administration disk it showes windows in the hda5 as an NTFS file system. I changed the hd0.4 to hd0.0 to see if that did anything, did't help.Thanks again everyone. Jim

---

### Post by jimmp226 on 2006-01-10
Ok I cant figure this out. When I restart the computer a window pops up to where you pick the operating system you want to start with. When I click on the windows option it says: can not read partition/ partition is not there .
 At the bottom of the menu.lst window I changed : hd0.0 thru hd0.5 and got the same type of messages. It will start into Ubuntu but I still cant get windows working. In Windows the partition is D: according to Ubuntu Windows is in hda5. 
 Sorry to take up so much time with this but I'm really stuck, I need windows to work. Any help would be greatly apperciated. Jim

---

### Post by J77 on 2006-01-11
[QUOTE=jimmp226] J77 I dont know what that is so I guess not. I paritationed my hard drive as follows:
C: Ubuntu
D: Windows XP
E: Cd Drive
F: External hard drive[/QUOTE]I'm not a Linux expert either, but I partitioned my hd as detailed in this post: [http://ubuntuforums.org/showthread.php?p=644696#post644696](http://ubuntuforums.org/showthread.php?p=644696#post644696)

I thought some space for the boot menu (grub) was needed to be assigned as /boot but I could be wrong...

:confused: :smile:

---

### Post by Irony on 2006-01-13
Post your;

*sudo fdisk -l*

Note when you post it enclose it in php marks (highlight the text and push the php button above). Like this;

[PHP]Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       20697   106502917+   5  Extended
/dev/hda3           20698       22451    14089005    c  W95 FAT32 (LBA)
/dev/hda4           22452       24792    18804082+  83  Linux
/dev/hda5            7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris
/dev/hda7           14619       16442    14651248+  83  Linux
/dev/hda8           16443       18509    16603146   83  Linux
/dev/hda9           18510       20697    17575078+  83  Linux

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes[/PHP]

---

