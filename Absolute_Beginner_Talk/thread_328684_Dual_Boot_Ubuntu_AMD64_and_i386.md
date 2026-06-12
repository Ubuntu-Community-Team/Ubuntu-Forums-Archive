---
title: "Dual Boot Ubuntu AMD64 and i386"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by michaeljustman on 2006-12-31
I recently decided to do a fresh install of Ubuntu (chronic problems with my wireless card)...

Anyway... I decided that while I was at it, I would move my boot partition to the beginning of my disk (I don't know why, exactly, but it looked weird in the middle of the disk) and install Ubuntu amd64 after I installed the i386 version (want to play with amd64 and get it working right before I switch over to it, instead of having to struggle with 'chroot'ing for media and proprietary codecs)

I left the old boot partition intact (thank God) and installed Ubuntu amd64 version after the i386 version.

The amd64 version made the new boot partition at the beginning of the disk (I had repartitioned and prepared the space before I installed i386 version.) and I was able to boot into the amd64 version from the grub menu.

Now... I have the old boot partition and the new boot partition. The kernel for amd64 is in the first partition and the i386 version is in the fourth. I was able to add items to menu.lst to allow me to boot into the i386 version, but I had to point it to the kernel on the fourth partition.

This is far from elegent... How do I put both kernels in the same boot partition, when they both have the same name?

---

### Post by opticalfiber on 2006-12-31
could you paste your menu.lst files in here from your both partitions and tell which pc do you have?

---

### Post by michaeljustman on 2006-12-31
1st boot partition (contains 64-bit kernel)
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
# kopt=root=UUID=76e45b9a-19d2-4270-a0ad-333dacc50838 ro
# kopt_2_6=root=/dev/hda8 ro

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


### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider.
# ones.
title		Ubuntu i386
root

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet
boot

# This is a divider.
# ones.
title		Ubuntu AMD64
root

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda8 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin
quiet
boot


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

Second boot partition (32-bit kernel)
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
# kopt=root=UUID=89508222-4c5d-4917-b2d3-514ed4696b0f ro
# kopt_2_6=root=/dev/hda6 ro

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,4)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,4)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/hda6 ro single
initrd		/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/memtest86+.bin
quiet
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

Partitions like this ||-Boot-||-Windows-||-Old-boot-||-Ubuntu32-||-Swap-||-Ubuntu64-||-Home-||

Computer is a HP Pavilion zv6000.
Sorry about the time between posts. It was 5am by the time I went to bed and I just woke up.

---

### Post by pseudonym on 2006-12-31
> **michaeljustman said:**
> This is far from elegent... How do I put both kernels in the same boot partition, when they both have the same name?
You can't, for that very reason. I've never tried what you want to do, but for it to work at all you would need to have differently-named kernels. In your case, this would mean hand-compiling at least one of your kernels, and uninstalling at least one of the default ones. Depending on your point of view, this is starting to sound even less elegant than what you've got now. ;)

Just a tip for running multiple Linux distros - One (and only one) /boot partition is indispensable, but you only really need to install grub once. during installation you have an option to 'proceed without installing bootloader' (or similar). Do that on the second and later OSes, and just edit /boot/grub/menu.lst manually with the details for the second and subsequent kernels. No need to have all your kernels in the same /boot directory, either. Grub will send its commands wherever you tell it to.

---

### Post by michaeljustman on 2006-12-31
Was thinking now... copy the old boot partition to my root partition for Ubuntu32 and point grub to that partition, can I delete the second boot partition? Do I just need the kernel files in the /boot directory of my Ubuntu32 install?

---

### Post by pseudonym on 2006-12-31
> **michaeljustman said:**
> Was thinking now... copy the old boot partition to my root partition for Ubuntu32 and point grub to that partition, can I delete the second boot partition? Do I just need the kernel files in the /boot directory of my Ubuntu32 install?
It sounds plausible, but TBH, I don't know. I'm not sure if other files in the system would be expecting to find the files in /boot/... where they are now.

But if you back everything up first, and don't delete your old boot partition yet, there should be no harm in trying to find out.

But I'm not responsible if you mess anything up, though ;)

---

### Post by michaeljustman on 2006-12-31
Awesome. Thanks so much for your help.

I got it working perfect now.

I put the kernel files physically in the partition where they belong in the /boot directory and pointed grub to the correct partition for each kernel. I mounted /dev/hda2 to the boot directory on each install of Ubuntu, so the the /boot/grub folder is available from both installs.

It's sort of like having the same named kernels in the same place. Now I can delete that old boot partition. :D

---

### Post by pseudonym on 2006-12-31
Cool :) GRUB is really flexible like that. You can even boot off of a logical partition if you want. ntldr blows compared to it.

---

### Post by michaeljustman on 2006-12-31
I'm just assuming that if I every recompile the kernel or download a new one from synaptic that it will overwrite the one that's there on the partition of the install and not the boot partition at the beginning of the disk... I think that since hda2 is mounted at /boot for each install it would write to hda2 and not hda5 or hda7...

Oh well... I'll just have to be careful when I do update the kernel, etc, that it writes it to the OS's partition and not to the boot partition, so I don't overwrite one of the others' kernels.

---

