---
title: "windows not loading"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by sam510 on 2007-09-16
alright im a complete noob at this so please try to explain it step by step. Well i installed linux on another partion on my HD, I really liked it it was like 10x better than windows but there was just some windows programs that linux wont support. I still wanna keep linux but i decided to go boot back into windows really quick. I chose the option to boot Windows NT/200/XP in the grub boot loader thing. It just says starting up......., It wont say anything else its just at the screen. I just want to know how to fix that problem. Maybe its trying to boot windows from the wrong partion or something i dont know. :[

---

### Post by mosiac on 2007-09-16
I think some of the advanced users will be able to help you more, but they are going to want you to probably post up your grub.conf file the steps to do this are pretty simple

Boot into linux, load up a console and in there type I THINK

vi /boot/grub/grub.conf (correct me if im wrong guys)

All the info that is in that file needs to be copy and pasted to this thread so we can see more about how grub was configured for your install.

I wish I could help more but this should get you started.

---

### Post by szymon_g on 2007-09-16
paste /etc/fstab and /boot/grub/menu.lst :P
have you got 1 or more discs? how many partitions etc?

---

### Post by sam510 on 2007-09-16
> **mosiac said:**
> I think some of the advanced users will be able to help you more, but they are going to want you to probably post up your grub.conf file the steps to do this are pretty simple

Boot into linux, load up a console and in there type I THINK

vi /boot/grub/grub.conf (correct me if im wrong guys)

All the info that is in that file needs to be copy and pasted to this thread so we can see more about how grub was configured for your install.

I wish I could help more but this should get you started.

I tried that but nothing really came up just lines.

---

### Post by Maestro23 on 2007-09-16
Open a terminal:

> cat /boot/grub/menu.lst (lower case L)

and

> cat /etc/fstab

Copy/Paste output from both commands here.

---

### Post by sam510 on 2007-09-16
sam@Sam-Desktop:~$ cat /boot/grub/menu.lst
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
default         0

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
# kopt=root=UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows NT/2000/XP (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

sam@Sam-Desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=14d22c5a-0c5b-41f4-97f0-3123a0b2cd00 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=2472858f-b17e-4a60-b820-5667e4a3bacf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
sam@Sam-Desktop:~$

---

### Post by Crafty Kisses on 2007-09-16
> **sam510 said:**
> alright im a complete noob at this so please try to explain it step by step. Well i installed linux on another partion on my HD, I really liked it it was like 10x better than windows but there was just some windows programs that linux wont support. I still wanna keep linux but i decided to go boot back into windows really quick. I chose the option to boot Windows NT/200/XP in the grub boot loader thing. It just says starting up......., It wont say anything else its just at the screen. I just want to know how to fix that problem. Maybe its trying to boot windows from the wrong partion or something i dont know. :[

I think you have to manually edit your Grub list, so Windows XP will appear.

---

### Post by szymon_g on 2007-09-16
seems ok to me :o

but i w'd change 
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

into this
.....
root (hd0,1)
....

i'm not sure that will help, but it wont harm system :P

have you got some hidden partitions (e.g. on my laptop was a hidden restore partition with ms windows xp)?

---

### Post by Crafty Kisses on 2007-09-16
> **szymon_g said:**
> seems ok to me :o

but i w'd change 
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1

into this
.....
root (hd0,1)
....

i'm not sure that will help, but it wont harm system :P

have you got some hidden partitions (e.g. on my laptop was a hidden restore partition with ms windows xp)?
That might help too.

---

### Post by sam510 on 2007-09-16
ok lol how do i do that.

---

### Post by Maestro23 on 2007-09-16
> **sam510 said:**
> ok lol how do i do that.

Need to edit the file. In terminal:

> gksudo gedit /boot/grub/menu.lst

Make the changes they told you to and save it.

---

### Post by sam510 on 2007-09-16
> **Maestro23 said:**
> Need to edit the file. In terminal:



Make the changes they told you to and save it.
ok well i did it but now it says Error 12: invalid device request when i try to boot windows. I think its the hd0,0 because before it was just be stuck at "starting up...." is there any other way i can fix it.

---

### Post by szymon_g on 2007-09-16
hm... so hd0,0 was a valid name for partition..  change /boot/grub/menu.lst back ...
i dont know why the problem occures :o but i'll write what i would do in situation like that:

1. defragmentation of windows' partitions <<- just in case
2. if it wouldn't help- i would 'fix' it making default windows' boot-manager (from windows installer cd)
3. i'd reinstall grub from ubuntu-alternate-cd
4. if it would'nt help- i would leave windows' bootmanager but i'd install grub on pandrive (but it is unsportsmanlike ;p)

---

### Post by sam510 on 2007-09-16
> **szymon_g said:**
> hm... so hd0,0 was a valid name for partition..  change /boot/grub/menu.lst back ...
i dont know why the problem occures :o but i'll write what i would do in situation like that:

1. defragmentation of windows' partitions <<- just in case
2. if it wouldn't help- i would 'fix' it making default windows' boot-manager (from windows installer cd)
3. i'd reinstall grub from ubuntu-alternate-cd
4. if it would'nt help- i would leave windows' bootmanager but i'd install grub on pandrive (but it is unsportsmanlike ;p)

alright can you please explain, the only thing i understood is making it the default windows bootmanager.(i dont have installer cd) How would i do the others?

---

### Post by sam510 on 2007-09-16
also do you guys think i might have messed up my windows installation?? i miss wow :[

---

### Post by sam510 on 2007-09-16
ehh can someone help me :[

---

### Post by sam510 on 2007-09-16
still no reply :[

---

### Post by Crafty Kisses on 2007-09-16
You didn't mess up you Windows installation, you just need to edit your Grub loader right, it takes time, wait for the replys.

---

