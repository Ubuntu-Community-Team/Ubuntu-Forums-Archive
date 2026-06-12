---
title: "Boot problem"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by Valok on 2007-12-11
So I recently want from a WUBI install, to giving Ubuntu its own partition, and installing it that way.  However, I was recently trying to install a splash screen via the tutorial here [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765) and when I tried to boot up again, it wouldn't go.

I had 4 Ubuntu options, something like 2.6.20-16 and 2.6.20-16 recovery (which is the part that is now not working) and also something like 2.6.20-15 and 2.6.20-15 recovery I am using 2.6.20.15 at the moment.

My question is, how do I go back and fix whatever I messed up in the first place?  And also what is the difference between these 2 options of linux, one which works, and one does not.

This is what it tells me when I try to boot.

"Kernal panic - not syncing: VFS: Unable to mount root on unknown-block (0,0)"

---

### Post by Valok on 2007-12-11
Bump, still having this problem and I dunno what to do! :(

---

### Post by Valok on 2007-12-11
Bump again

---

### Post by p_quarles on 2007-12-11
It's generally discouraged to bump a thread more than once every twenty four hours. Be patient. :)

Anyway, the difference between the two versions: they are different kernels. If the old kernel (2.6.20-15) is working okay for you, there's really no reason not to use it. 

If you want that kernel to automatically load by default, I can give you the steps you'll need. If you could post the output of the following command, I can tell exactly what to do:
```
cat /boot/grub/menu.lst
```

---

### Post by confused57 on 2007-12-11
> **Valok said:**
> So I recently want from a WUBI install, to giving Ubuntu its own partition, and installing it that way.  However, I was recently trying to install a splash screen via the tutorial here [https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765) and when I tried to boot up again, it wouldn't go.

I had 4 Ubuntu options, something like 2.6.20-16 and 2.6.20-16 recovery (which is the part that is now not working) and also something like 2.6.20-15 and 2.6.20-15 recovery I am using 2.6.20.15 at the moment.

My question is, how do I go back and fix whatever I messed up in the first place?  And also what is the difference between these 2 options of linux, one which works, and one does not.

This is what it tells me when I try to boot.

"Kernal panic - not syncing: VFS: Unable to mount root on unknown-block (0,0)"
You could try highlighting your Ubuntu 2.6.20-16 kernel entry in the grub boot menu, press "e" to edit, then highlight the line with kernel, press "e" again, then remove anything in the kernel line that you added(e.g. vga=791), press "enter", then "b" to boot.  This change is temporary, if it works; but may be worth trying & can be made permanent.

---

### Post by Valok on 2007-12-11
Sorry for the bumpage, but thanks for letting me know what the norm on that is =)

Anyways, here is the output from the command you suggested
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

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
# root          (hd0,1)
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
# kopt=root=UUID=d855fea4-d075-4b35-84dd-6a61080b17a0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d855fea4-d075-4b35-84dd-6a61080b17a0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d855fea4-d075-4b35-84dd-6a61080b17a0 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d855fea4-d075-4b35-84dd-6a61080b17a0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d855fea4-d075-4b35-84dd-6a61080b17a0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


title Windows
root (hd0,0)
makeactive
chainloader +1
boot

```

---

### Post by p_quarles on 2007-12-11
Cool. Here's how you can set the old kernel to boot up automatically. First backup the boot menu:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Now, you'll need to edit the original file:
```
gksudo gedit /boot/grub/menu.lst
```
Change the line that says:
```
default 0
```
(it's near the top of the file) to:
```
default 2
```
Reboot, and you should be good. In case it doesn't work right, though, you've backed up the old file. Just to be safe.

---

### Post by Valok on 2007-12-11
Cool!  Still brings me to the grub menu, but it selects the working kernel to boot up off of right off the bat.

I have another side question that is sort of related.  Today I made a partition in order to install Ubuntu on (from a WUBI install).  I know I made the partition right, and used LVPM to transfer all my files.

However, I heard somewhere that if you still have a /host file (which I do) then the install is still a WUBI install.  The hard drive icon on my desktop is also called "host0".  Not sure if this is alright, or means I didn't quite finish the full install.

---

### Post by p_quarles on 2007-12-11
I don't know much about Wubi, but I'm *guessing* that's a virtual drive that's inside your Windows partition. Your Ubuntu installation is fine; I think it's just the Wubi installation inside Windows that wasn't fully uninstalled.

---

### Post by choisj70 on 2007-12-12
Try QGRUBEditor from the link I attached below.

[http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391](http://www.qt-apps.org/content/show.php/QGRUBEditor?content=60391)

You can download it for UBUNTU. Installation will be automatic. Editing GRUB has been easy and safe so far.

---

