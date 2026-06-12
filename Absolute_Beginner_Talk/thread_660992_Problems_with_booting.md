---
title: "Problems with booting"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by benji.ijneb on 2008-01-07
When ubuntu boots up, after loading grub, i get an error message telling me that there is a kernel panic and root cant mount to foreign block. (or someting like that)

i booted up the livecd and fiddled around with menu.lst (no major changes though)
i did notice this:

> 
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
 

it claims that root is (hd0,0) when i remember it not being that previously (sorry if all this is a bit vague p.s. I was doing other changes to menu.lst before whhich may somehow have caused this (they were only minor, unimportant changes))

so my question is, how do I find out what that number is supposed to be? 
thanks

---

### Post by eternicode on 2008-01-07
First off, when messing around in config files, *no* change is unimportant. ;)

To find the correct "root", open up a console and issue the "grub" command.
```

$ grub

grub>

```
From within the grub shell, try
```

grub> find /boot/grub/stage1

```
Unless you have a separate grub boot partition, this should return the (hdX,X) that you're looking for.

If you know the filename of the kernel referrenced from menu.lst, you could also use that:
```

grub> find /boot/<kernel-filename>

```

When you're done, type "quit" from the grub shell to exit to a normal prompt.

---

### Post by maruchan on 2008-01-07
You can boot up a disk with partitioning software on it (like Puppy Linux or so with gParted) and check the partitions. 0,1 means "first disk, second partition" (counting from 0) and 0,0 means "first disk, first partition.

---

### Post by benji.ijneb on 2008-01-07
turns out that it actually IS (hd0,0)
so...now what?

---

### Post by eternicode on 2008-01-07
Could you post the exact error message?

Also, if you can get to it, post your installation's /etc/fstab file.

```

cat /etc/fstab

```

---

### Post by benji.ijneb on 2008-01-07
> **eternicode said:**
> Could you post the exact error message?

Also, if you can get to it, post your installation's /etc/fstab file.

```

cat /etc/fstab

```

thanks for all your help so far:

/etc/fstab:
> # /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda1 
UUID=60a1113e-2e98-4df3-8d88-5335beffb760 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/sda5 
UUID=ce125768-c83c-4826-a25f-25db63ff10c8 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


menu.lst (just in case)
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
# WARNING: If you are using dmraid do not use 'savedefault' or your 
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/ 
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
# kopt=root=UUID=60a1113e-2e98-4df3-8d88-5335beffb760 ro 
 
## Setup crashdump menu entries 
## e.g. crashdump=1 
# crashdump=0 
 
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
 
## additional options to use with the default boot option, but not with the 
## alternatives 
## e.g. defoptions=vga=791 resume=/dev/hda5 
# defoptions=vga=775 splash quiet 
 
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
 
## should update-grub add savedefault to the default options 
## can be true or false 
# savedefault=false 
 
## ## End Default Options ## 
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=60a1113e-2e98-4df3-8d88-5335beffb760 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic 
quiet 
 
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) 
root		(hd0,0) 
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=60a1113e-2e98-4df3-8d88-5335beffb760 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic 
 
title		Ubuntu 7.10, memtest86+ 
root		(hd0,0) 
kernel		/boot/memtest86+.bin 
quiet 
 
### END DEBIAN AUTOMAGIC KERNELS LIST 


error message:
> invalid compressed format
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block

hope this helps!

---

### Post by eternicode on 2008-01-07
Everything looks fine from here, unless the UUID in your fstab doesn't match the UUID of your actual root partition (which it should, unless it was modified).  You can check this by matching the UUID in your fstab against the UUID given by
```

$ blkid /dev/sda1

```

I'm guessing you'll probably have to reinstall Ubuntu.  Might try reinstalling grub first, though.

---

### Post by benji.ijneb on 2008-01-07
> **eternicode said:**
> Everything looks fine from here, unless the UUID in your fstab doesn't match the UUID of your actual root partition (which it should, unless it was modified).  You can check this by matching the UUID in your fstab against the UUID given by
```

$ blkid /dev/sda1

```

I'm guessing you'll probably have to reinstall Ubuntu.  Might try reinstalling grub first, though.

thanks so much - i'll do that tomorow (yawn)

two more things:
1: how do i reinstall grub on my HD from the live cd?
2:if i do have to reinstall ubuntu, is there any way of keeping my user settings, installed programes etc?

also, it would be much appreciated if you were to sighn up for email alerts on this post - in case i have more problems (lets hope not)

thank you so much for all your help

---

### Post by eternicode on 2008-01-07
> **benji.ijneb said:**
> 
1: how do i reinstall grub on my HD from the live cd?


[HOWTO: Reinstall GRUB (if your MBR is messed up)]("http://ubuntuforums.org/showthread.php?t=24113")

> **benji.ijneb said:**
> 
2:if i do have to reinstall ubuntu, is there any way of keeping my user settings, installed programes etc?


Settings, yes; programs, no.

[HOWTO: Move /home and secure your files and configuration]("http://ubuntuforums.org/showthread.php?t=46866")

> **benji.ijneb said:**
> also, it would be much appreciated if you were to sighn up for email alerts on this post - in case i have more problems (lets hope not)

No worries; my settings automatically subscribe me to threads I've posted to ;)

---

