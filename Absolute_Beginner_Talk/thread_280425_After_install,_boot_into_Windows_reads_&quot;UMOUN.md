---
title: "After install, boot into Windows reads &quot;UMOUNTABLE_BOOT_VOLUME&quot;"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by Oyjord on 2006-10-19
Hi all,

I'm still really new to all this, please bear with me.

I installed Ubuntu, love it to death, and it works great.

However, when I boot my comp and choose my Windows XP OS in GRUB, I get a BSOD reading "UNMOUNTABLE_BOOT_VOLUME."

Here's something weird, though.  If I FIRST boot into Ubunutu, then restart, then choose my Windows install, I boot into Windows just fine.  Very weird.

Here's my /boot/grub/menu.lst if it might help:

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
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

 

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
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


```

Thanks a bunch for the help.
Oyjord.

---

### Post by gn2 on 2006-10-19
My suggestion would be to run "fixmbr" from recovery mode on your windows disc, and install Grub on a floppy?

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I've never done the grub on a floppy thing but it is a good option.

---

### Post by Oyjord on 2006-10-19
Thanks a bunch for the reply.  Being a newb, I've no clue what fixmbr is, and since we're dealing with some important stuff, here, I don't want to go around and mess things up ;)

Especially since I can boot into Windows just fine AFTER booting into Ubuntu.  Isn't that strange?  That has to be indicative or a particular problem in my config.

Any other suggestions would be greatly appreciated.

Thanks a bunch,
Oy.

---

### Post by gn2 on 2006-10-19
Insert Windows CD. Re-boot, select recovery, enter fixmbr at the prompt press enter, cross fingers, pray.

It is a utility that will re-write the Master Boot Record.

Doesn't always work.

Super grub disc is a useful tool: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

---

### Post by Oyjord on 2006-10-19
> **gn2 said:**
> Insert Windows CD. Re-boot, select recovery, enter fixmbr at the prompt press enter, cross fingers, pray.

It is a utility that will re-write the Master Boot Record.

Doesn't always work.

Super grub disc is a useful tool: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

Thanks, I'll try these out.  However, if I do rewrite the MBR, does that then mean I won't have a dual bootable machine?  Does that mean I then won't be able to boot into Ubuntu?

Thanks again,
Oy.

---

### Post by gn2 on 2006-10-19
> **Oyjord said:**
> Thanks, I'll try these out.  However, if I do rewrite the MBR, does that then mean I won't have a dual bootable machine?  Does that mean I then won't be able to boot into Ubuntu?

Thanks again,
Oy.

Yes if you "fixmbr" you will need to arrange a boot facility for Ubuntu.

Super grub disc can do that for you.

---

