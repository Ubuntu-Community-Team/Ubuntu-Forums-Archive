---
title: "Black Screen on startup"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by semperfiguy on 2007-04-13
Hey, I have been having this problem on and off in edgy, but I just upgraded to Fiesty and now it happens every time I use kernel 2.6.20-386.  Im running a dell inspiron 1100 laptop and whenever I boot it up, it gets by all the starting of services.  When it is supposed to go into GDM all I get is a black screen.  I can't alt-ctrl-f1 into a terminal, the only way I can restart is holding down the power button.

But when I start in recovery mode as soon as it gets to the root login I type exit and it goes through the rest of the services and gdm starts fine.  I have no idea what the problem is, could anyone help me with this?

---

### Post by pxwpxw on 2007-04-13
Hi,
 when you start in recovery mode,
```

uname -a

```
to see if that is the new kernel version.

---

### Post by semperfiguy on 2007-04-13
```

semperfiguy@ubuntuPortable:~$ uname -a
Linux ubuntuPortable 2.6.20-14-386 #2 Mon Apr 2 20:34:35 UTC 2007 i686 GNU/Linux

```

I posted this in the morning before I got the updates.. so I will have to try the new kernel and see if it fixes this.

---

### Post by pxwpxw on 2007-04-13
Well, I am not sure if that proves anything yet, I dont have fiesty here.
I was thinking maybe you are getting a different kernel version for recovery and normal start.
Have a look at /boot/grub/menu.lst to see what it says for the normal and recovery versions.

---

### Post by semperfiguy on 2007-04-14
Well I did an update to kernel 2.6.20-14 and it worked the first reboot, but now its back to the same old thing.  I have to go to recovery mode to get to the GDM login screen. otherwise its just a black  screen and no control.

Here is my /boot/grub/menu.lst
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro

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
# defoptions=splash quiet rootflags=data=writeback vga=773

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
# altoptions=(recovery mode) single rootflags=data=writeback

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=4

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-386 root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro splash quiet rootflags=data=writeback vga=773
initrd		/boot/initrd.img-2.6.20-14-386
savedefault

title		Ubuntu, kernel 2.6.20-14-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-386 root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-14-386

title		Ubuntu, kernel 2.6.20-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro splash quiet rootflags=data=writeback vga=773
initrd		/boot/initrd.img-2.6.20-14-generic
savedefault

title		Ubuntu, kernel 2.6.20-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-generic root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.20-14-generic

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro splash quiet rootflags=data=writeback vga=773
initrd		/boot/initrd.img-2.6.17-11-386
savedefault

title		Ubuntu, kernel 2.6.17-11-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-11-386

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro splash quiet rootflags=data=writeback vga=773
initrd		/boot/initrd.img-2.6.17-11-generic
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by pxwpxw on 2007-04-14
Backup your menu.lst then try some variations. 

You seem to have 4 kernel versions listed, not sure what you are booting. Check /boot to see.
Try them all.
I dont know if there are any issues with the new kernel version.

When the grub menu comes up, hit the 'e' key and you can try changes (read what it says) 
Or you can just edit menu.lst. after making a backup.

> 
title		Ubuntu, kernel 2.6.20-14-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-14-386 root=UUID=2f35db4d-12e2-433b-8488-6eb8785e9770 ro splash quiet rootflags=data=writeback vga=773
initrd		/boot/initrd.img-2.6.20-14-386
savedefault


Try 1+2 and 1+2+3 of these:

1. delete the 'vga=773'
2. delete the 'splash quiet'
3. delete the 'rootflags=data=writeback' (but I dont know what that does).

---

### Post by semperfiguy on 2007-04-14
I know the VGA=773 and splash quiet are for the boot splash screen.   I would like to keep that on but I'll try it to see if it makes a difference.  The other part (3.) was from some tweaks I followed from here ([http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/](http://kmandla.wordpress.com/2006/11/11/howto-set-up-edgy-for-speed/))

> 
File system tweaks

Two more tweaks to the file system will keep your ext3 machine running fast: The journal_data_writeback option, and the noatime option. We need to set these in Grub, in fstab, and by enabling the option with tune2fs.

First, open the Grub boot menu.

    sudo nano -w /boot/grub/menu.lst

Look for the two options sections, and edit them to look like this. (Important: Leave that initial hash mark in there!)

    # defoptions=rootflags=data=writeback elevator=cfq

And this. (Important: Leave that initial hash mark in there!)

    # altoptions=(recovery mode) single rootflags=data=writeback elevator=cfq

Under defoptions, I took out splash and quiet. First, I like to see the terminal commands scroll by, so I don’t want the quiet option. Second, there’s no splash screen to speak of, so it’s safe to take that out.

root=data=writeback is the file system option we’re going to set. elevator=cfq is another tweak that adjusts the queueing. It sometimes gives me a tiny improvement, depending on the hardware and the I/O load.

Since we’ve altered the boot options, we need to update Grub.

    sudo update-grub

Now let’s alter the fstab so it expects those options. Enter this into a terminal.

    sudo nano -w /etc/fstab

This part is a little tricky. Edgy assigns a smear of UUID codes to the fstab entries, which makes them a little difficult to manage. Alter your lines for /dev/hda2 and /dev/hda4 like this.

    # /dev/hda2
    UUID=82eaeb0f-9df6-4129-a075-d98657d2e619 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0
    # /dev/hda4
    UUID=8725b47c-c92e-48bb-9aa7-32ee39befc35 /home ext3 defaults,data=writeback,noatime 0 2

It’s possible your UUID numbers will be different, so don’t just cut-and-paste these lines into your fstab. Add the data=writeback and noatime flags to those partitions, where you see the defaults term.

Now that both Grub and fstab are ready, we can add the actual flag to the file systems.

    sudo tune2fs -o journal_data_writeback /dev/hda2
    sudo tune2fs -o journal_data_writeback /dev/hda4

Excellent! Now we’re ready to move on.



I could undo that to see if it changes anything.  Heres something I just tried. if I boot from recovery mode and do a restart, it works but if I do a shutdown, it doesn't.  I dont know what that means though.

---

### Post by pxwpxw on 2007-04-14
Try it without the tweaks and get your desktop running nicely, then do what tweaks you want after you know its ok with the new kernel.

---

