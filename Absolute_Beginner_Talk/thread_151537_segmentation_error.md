---
title: "segmentation error"
date: 2006-03-28
forum: Absolute Beginner Talk
---

### Post by lex1 on 2006-03-28
Just installed sarge on hda1 and get error with segmentation fault
(6) journal block device drive loaded

pivot_root: no such file or directory
/sbin/init: 432 cannot open dev/console no such file

kernnel panic attempted to kill init


hda1 sarge (ext3)

hda2 swap

had3 ubuntu (ext3)

hda4 extentended 

hda5 swap

---

### Post by Pragmatist on 2006-03-29
Can you still boot into Debian Sarge?  

If so, please show us BOTH of your /boot/grub/menu.lst files, one for Debian Sarge and one for Ubuntu

What were your partitions before installing Ubuntu? In general, how did you go about installing Ubuntu?

---

### Post by lex1 on 2006-03-30
fist of all here is the disk layout

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2690    21607393+  83  Linux
/dev/hda2            2691        2809      955867+  82  Linux swap / Solaris
/dev/hda3            2810        4776    15799927+  83  Linux
/dev/hda4            4777        4864      706860    5  Extended
/dev/hda5            4777        4864      706828+  82  Linux swap / Solaris


There was a small fat partition of 2mb with the various files which came built into the labtop it was some files to aid the installation of XP home in my acer traelmate 2200 this was /dev/had1 on /dev/hda2 there was a xp home os fat32.
Ubuntu on /dev/hda3 has been intalled from BB 5-10 CD about january 2005
no probs with install. 

It was all controled by ubuntu grub but now sarge grub is installed can boot
into ubuntu no problems below is menu.list for ubuntu and below that is menu .list for sarge.
I can start the boot into sarge but stops at the point where I get the error message as posted
in my fist post of this thread. 

#
Lex1:
--------------------------------------------------------------
ubuntu  menu list
 # menu.lst - See: grub(, info grub, update-grub()
#            grub-install(), grub-floppy(),
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
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
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
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
# on /dev/hda2
title		Microsoft Windows XP Home Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

----------------------------------------------------------------------------------------------------
sarge menu list

# menu.lst - See: grub(), info grub, update-grub()
#            grub-install(), grub-floppy(),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0,
and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default
entry
# is the entry saved with the command 'savedefault'.           
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default
entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive
editing
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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title        Debian GNU/Linux, kernel 2.4.27-2-386
root        (hd0,0)
kernel        /boot/vmlinuz-2.4.27-2-386 root=/dev/hda1 ro
initrd        /boot/initrd.img-2.4.27-2-386
savedefault
boot

title        Debian GNU/Linux, kernel 2.4.27-2-386 (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.4.27-2-386 root=/dev/hda1 ro single
initrd        /boot/initrd.img-2.4.27-2-386
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, kernel 2.6.12-10-386 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, kernel 2.6.12-9-386 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, kernel 2.6.12-9-386 (recovery mode) (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Ubuntu, memtest86+ (on /dev/hda3)
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot

---

### Post by Pragmatist on 2006-03-30
Ok, as I'm understanding it:
 ---------------------------------------------------------------------------------------------------------
 **Before Linux:**
  1.)  You had a special XP partition on /dev/hda1
  2.)  You had winXP on /dev/hda2 
 ---------------------------------------------------------------------------------------------------------
  **Only Ubuntu Breezy:**
 I'm assuming you had this on /dev/hda1 and **everything worked?**
 ---------------------------------------------------------------------------------------------------------
 **Currently--Debian Sarge & Ubuntu Breezy:**
  1.) /dev/hda1  ~ 21.6 GB     Debian Sarge    bootable (*)
  2.) /dev/hda3  ~ 15.8 GB     Ubuntu Breezy 
  
  You can't boot into Debian Sarge     You get the error message you posted
  You can't [B]boot into Ubuntu Breezy   What happens here?
[/B]---------------------------------------------------------------------------------------------------------
 
 My advice depends on your giving more complete information.
 If you can boot into Ubuntu, can you mount the /dev/hda1 partition and see the filesystem of Debian Sarge?  If so, send some information like /var/log/syslog

---

### Post by lex1 on 2006-03-30
ok just to clear up

bb has never been on /dev/hda1 only xp
now sarge is on /dev/hda1

bb has always been on dev/hda3
can and always have have  been able to boot into bb 5-10

lex1

---

### Post by Pragmatist on 2006-03-30
> Originally Posted by: **lex1**
 **can** and always have have  been able to **boot into bb 5-10**


> Originally Posted by: **Pragmatist**
**If you can boot into Ubuntu**, can you mount the /dev/hda1 partition and see the filesystem of Debian Sarge? If so, send some information like /var/log/syslog

Can you do this?

---

### Post by lex1 on 2006-03-30
loks like its empty


lex1@xstation:/mnt/var/log$ ls -la
total 28
drwxr-xr-x   6 root   root  4096 2006-03-28 09:32 .
drwxr-xr-x  13 root   root  4096 2006-03-28 09:24 ..
-rw-r-----   1 root   adm      0 2006-03-28 09:29 auth.log
-rw-rw-r--   1 root   utmp     0 2006-03-28 09:24 btmp
drwxr-xr-x   3 root   root  4096 2006-03-28 09:32 debian-installer
drwxr-s---   2 syslog adm   4096 2006-03-28 09:28 exim4
drwxr-xr-x   2 root   root  4096 2006-03-28 09:26 ksymoops
-rw-rw-r--   1 root   utmp 30076 2006-03-28 09:28 lastlog
drwxr-sr-x   2 news   news  4096 2006-03-28 09:29 news
-rw-r-----   1 root   adm      0 2006-03-28 09:29 syslog
-rw-rw-r--   1 root   utmp     0 2006-03-28 09:24 wtmp

---

