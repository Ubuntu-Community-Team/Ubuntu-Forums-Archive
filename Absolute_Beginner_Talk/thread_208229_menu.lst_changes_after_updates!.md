---
title: "menu.lst changes after updates!"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by headsh0t13 on 2006-07-03
I`m sick of it. Every time I install any updates, my menu.lst changes and the Windows XP doesn`t show up in the OS menu during boot up. So I have to edit it manually. 
Is there any way i can get notified when it changes?, or at least deny any changes to menu.lst

Thnx


PS
I`m using: 6.06 LTS

---

### Post by jrib on 2006-07-03
[QUOTE=headsh0t13]I`m sick of it. Every time I install any updates, my menu.lst changes and the Windows XP doesn`t show up in the OS menu during boot up. So I have to edit it manually. 
Is there any way i can get notified when it changes?, or at least deny any changes to menu.lst

Thnx


PS
I`m using: 6.06 LTS[/QUOTE]

I've gotten a new kernel added to my menu.lst and it doesn't seem to touch the windows part.  Maybe you can post what your menu.lst looks like?

This is mine:

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
default         1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         5

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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

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

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-686 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-25-686
boot

title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by adam.tropics on 2006-07-03
I may be wrong, but as far as I am aware, it will update only when either a new kernel is installed, grub is updated, or if you install grub artwork.

---

### Post by mcduck on 2006-07-03
When you edit menu.lst, notice these lines:
```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST

```
Everything between them will be modified when you get a kernel update. If you add any extra entries to menu.lst, like the one for Windows, make sure that they are either before or after this section..

---

### Post by headsh0t13 on 2006-07-03
Ok, lets forget about menu.lst

I`m going to do a:
```
fdsik /MBR
``` 
And I think this is going to remove GRUB.
I guess this means I`ll have to use Windows until I find an other alternative.

So, Is there a way to let Windows manage the OS menu?.

---

### Post by drtvasudevan on 2006-07-03
install a third party boot loader like xosl which i use.
you can install this from windows and also restore it if and when needed.
i put all the grub in the linux partition itself.

hope this helps

tv

---

### Post by vayu on 2006-07-04
[QUOTE=headsh0t13]I`m sick of it. Every time I install any updates, my menu.lst changes and the Windows XP doesn`t show up in the OS menu during boot up. So I have to edit it manually. 
Is there any way i can get notified when it changes?, or at least deny any changes to menu.lst

Thnx


PS
I`m using: 6.06 LTS[/QUOTE]


As another poster pointed out, make sure your Windows entry is outside of the begin/end automagic kernels list.  Also if you want your default to stay on the same entry even though new kernel options are added after a kernel update or reconfigure you can uncomment the line "updatedefaultentry=false" 
EDIT: and change to "true" as shown here:

## should update-grub adjust the value of the default booted system
## can be true or false
updatedefaultentry=true

It's good after a kernel upgrade to have the old kernel still show up as an option because the new one might not work.  If that happens then you can reboot and use the old one.  Once you're happy with the new kernel then you can go in and delete the old entries.

If you do those two things, then when a kernel update does change your menu.lst it won't be much of an inconvenience and you can take your time to delete the old entries.

---

