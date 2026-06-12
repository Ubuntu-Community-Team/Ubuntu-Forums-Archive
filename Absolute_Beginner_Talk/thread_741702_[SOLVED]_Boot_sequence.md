---
title: "[SOLVED] Boot sequence"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by OlyPerson on 2008-04-01
Ok, I am having somewhat of an issue.  I am not dual booting, but still have to choose my system by pressing esc shortly after the BIOS thing goes away on booting.  Here, I can select from a series of option that I think go something like
```
Ubuntu 7.10, kernel 2.6.22-14-386
Ubuntu 7.10, kernel 2.6.22-14-386(recovery mode)
Ubuntu 7.10, kernel 2.6.22-14-generic
```
etc, etc
The thing is, is that I think it boots automatically into the Ubuntu 7.10, kernel 2.6.22-14-386 one, and in that 'version' (not sure what to call it) my internet doesn't work along with some other things.  So every time I boot I have to choose the Ubuntu 7.10, kernel 2.6.22-14-generic version which does work.  How can I make it boot this automatically?
Thanks, this has been kind of annoying me and I tried to do it myself by editing my menu.lst file, but it didn't work (at least, what I did didn't work)

---

### Post by joshrobinson on 2008-04-01
could you post the contents of your menu.lst file?

```
gedit /boot/grub/menu.lst
```

---

### Post by kbless7 on 2008-04-01
Reorder your grub list so that the kernel you want is listed first. Thats how it will show up in grub, thus defaulting to the first kernel listed.

---

### Post by joshrobinson on 2008-04-01
> **kbless7 said:**
> Reorder your grub list so that the kernel you want is listed first. Thats how it will show up in grub, thus defaulting to the first kernel listed.
 
or just change the default number, thats why i was asking to see the OP's menu.lst
but either way works

---

### Post by OlyPerson on 2008-04-01
> **joshrobinson said:**
> could you post the contents of your menu.lst file?

```
gedit /boot/grub/menu.lst
```

I get:
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
# kopt=root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##
title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```


I tried changing it to this so the generic option is first: (the last bit)
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-386
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro single
initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```
but I didn't delete the second
```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```
when I put it at the top.
Doing this made it kind of boot, but it got hung up at one point and it wasn't the same.

---

### Post by mcduck on 2008-04-01
Why not just uninstall the 386-kernel? You don't need it, it doesn't work for you, and it's only eating your disk space.. Simply go to Synaptic and uninstall it and it will be automatically removed from the Grub menu as well.

(By the way, reordering items in the menu.lst is not a good way to change the boot order. When you get a kernel update the whole section marked as "debian automagick kernel list" will be automatically overwrited, and you'll have to reorder it again and again yourself. But if you change the default number instead the change will stay even through kernel updates.)

---

### Post by OlyPerson on 2008-04-01
You sure that that is the case?  I mean it seems that I couldn't have two OS's on there; my hard drive is only 4GB.  Second opinion?

---

### Post by mcduck on 2008-04-01
> **OlyPerson said:**
> You sure that that is the case?  I mean it seems that I couldn't have two OS's on there; my hard drive is only 4GB.  Second opinion?

Having another kernel is no the same as having another OS. Your menu.lst clearly lists two different kernels, 386-kernel and generic kernel. The generic kernel works for almost any modern CPU so the 386-kernel is not needed.

---

### Post by shadowtroopers on 2008-04-01
I agreed with that, just go to synaptic package manager and remove Ubuntu 7.10, kernel 2.6.22-14-386, the only thing we need is only Ubuntu 7.10, kernel 2.6.22-14-generic.

---

### Post by msak007 on 2008-04-01
Yup I agree, get rid of the i386 kernel and stick with the generic kernel which works for you (especially since your partition is only 4 GB). You really only need 1 kernel. Usually when there's a kernel update I keep the current one and the one before it in case of any problems with the update, and get rid of everything else. But having 2 same # kernels for different architectures is unnecessary and a waste of space.

---

### Post by thisiam on 2008-04-01
Would changing the menu.lst to this work?
this is what i did and now i just have to pick between windoze and ubuntu, 10 sec and loads ubuntu so i am happy.



## ## End Default Options ##
#title		Ubuntu 7.10, kernel 2.6.22-14-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c #ro quiet splash
#initrd		/boot/initrd.img-2.6.22-14-386
#quiet

#title		Ubuntu 7.10, kernel 2.6.22-14-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.22-14-386 root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c #ro single
#initrd		/boot/initrd.img-2.6.22-14-386

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=abeacc99-26e4-4904-bd6a-3488eded7d2c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

#title		Ubuntu 7.10, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by OlyPerson on 2008-04-01
Ok!  Deleting the -386 kernel worked and now all is well, thanks!

---

