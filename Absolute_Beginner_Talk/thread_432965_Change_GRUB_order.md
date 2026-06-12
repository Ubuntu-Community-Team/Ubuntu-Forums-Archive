---
title: "Change GRUB order"
date: 2007-05-04
forum: Absolute Beginner Talk
---

### Post by carrie.peary on 2007-05-04
Basically, I have 6 linux kernel options to choose from and my windows one too. I want to have Windows be first to boot (currently not), and get rid of any of the other kernels that I have listed that I really don't need (probably like 4 of them). 

I surfed the web and this forum but nothing I didn't figure it out from them....anyways, here is my menu.lst (I backed it up, just fyi)......thanks to anyone that can help ^_^

-----------------------------------------------------------------------------------------------------------

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

// Password stuff was here, but deleted for posting

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
# kopt=root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

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

---

### Post by carrie.peary on 2007-05-04
The smilies above are really "8" but I couldn't get them to go away in the post.

---

### Post by Pobega on 2007-05-04
```
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

// Password stuff was here, but deleted for posting

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1


title Ubuntu, kernel 2.6.20-15-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, kernel 2.6.17-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd /boot/initrd.img-2.6.17-11-generic

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=UUID=b6784c25-6501-44ce-bce2-ac9a45c0f817 ro single
initrd /boot/initrd.img-2.6.17-10-generic

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root
```

That puts Windows first. As for removing kernels, don't just remove them from menu.lst, use dpkg to uninstall them from your system (Your menu.lst should automagically update thanks to Debian's awesome handling of GRUB's configuration files.)

---

### Post by 3rr0r on 2007-05-04
You could just comment out all the "extra" kernerls and memory tests (just put # in front of each line)

---

### Post by carrie.peary on 2007-05-04
Thanks guys! It works!!!! And I didn't know that I could uninstall them.....did that too.

---

### Post by Pobega on 2007-05-04
> **3rr0r said:**
> You could just comment out all the "extra" kernerls and memory tests (just put # in front of each line)

That wouldn't really remove them from the system though, I mean if you have no use for the kernel then why leave it wasting space on the host system?

---

### Post by confused57 on 2007-05-04
You could also place your Window's entry above the line  "BEGIN AUTOMAGIC KERNELS LIST", keep your default as 0 & Window's will boot first.

To limit the number of kernels listed, you could change the line #howmany=2, or however many kernels you want displayed...as someone else mentioned, you could comment(#) the kernels you don't want displayed.

You can uninstall the unwanted kernels from Synaptic, search for "linux-image" & select to remove the kernels you no longer want.

---

