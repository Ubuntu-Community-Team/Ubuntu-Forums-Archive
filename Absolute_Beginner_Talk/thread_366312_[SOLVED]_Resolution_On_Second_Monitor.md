---
title: "[SOLVED] Resolution On Second Monitor"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by Sklasko on 2007-02-20
Ok, here's the thing, I recently decided to connect an old CRT monitor I have to my laptop and, with other devices, essentially use it as a desktop. However, my only problem is that when Ubuntu is booting, it uses the native 1280x768 resolution making it hard for me to see all the boot information.

I have tried using "sudo dpkg-reconfigure xserver-xorg" to get rid of the 1280x768 resolution but since the boot process isn't in X, this doesn't help.

Anyway around this? :-k Thanks for any help in advance.

---

### Post by veloce on 2007-02-20
I can't quite follow what your problem is.  Do you just need a lower resolution on the CRT under X?

If so:
[LIST=1]
[*]boot up using the laptop screen
[*]lower the screen resolution within X
[*]shutdown
[*]boot up using the crt - it should now use the lower resolution
[/LIST]

---

### Post by Sklasko on 2007-02-21
What I mean is, the boot process. When your booting the computer and it shows the progress of starting all the processes and services.

I can get the correct resolution under X, just not before X starts up.

---

### Post by 42Wired on 2007-02-21
My second monitor also has this problem. It cuts off the bottom and the right side during boot and in console mode. I don't think there is anything that can be done about it (but I could be wrong), because it does the same thing for me in Windows during boot.

EDIT: Can you maintain separate resolutions for your monitors? I would like to keep my second one in its native resolution.

---

### Post by Liger_XT5 on 2007-02-21
Next to the login and pass, there is a picture that when clicked, it brings down a menu.
click restart X.

I did have this problem until I did that, and things are fine.
So I hope that helps.

---

### Post by 42Wired on 2007-02-21
There's no picture for mine, although I'm running Dapper.

---

### Post by Sklasko on 2007-02-24
> **42Wired said:**
> EDIT: Can you maintain separate resolutions for your monitors? I would like to keep my second one in its native resolution.

Sorry for the late reply, but no, the ATI control panel that comes with the drivers doesn't really do anything so I can't have them use different resolutions or set the CRT to be the primary monitor. It's just a waste of harddrive space. Of course this only applies to ATI users, I can't speak for Nvidia.

---

### Post by mgmiller on 2007-02-24
How to change the resolution during the graphical boot:

You need to edit /boot/grub/menu.lst and add vga=771 or 788 or 792 
to the end of the line for the kernel you are booting.

First make a backup of the old one:

```
sudo cp /boot/grub/menu.lst menu.lst.backup
```

Then edit the file:
```

sudo gedit /boot/grub/menu.lst
```

Once you have the vga= number you like, add it to the automagic line options 
in the additional options area so it carries through to kernel updates. 
This is in /boot/grub/menu.lst as shown below, where I have selected vga=786,
which will set the boot screen to 640x480 24 bit color:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=786

Finally, to append the change to all kernel lines, run the following: 
 
```
 sudo update-grub 
```

To know which vga= number to use, consult this handy chart:

640x480    800x600    1024x768    1280x1024
......768...........771.............773...........775.................256 colors
......784...........787.............790...........793.................(8 bit)
......785...........788.............791...........794.................(16 bit)
......786...........789.............792...........795.................(24 bit)

---

### Post by 42Wired on 2007-02-25
After I add the line, update, and restart, it still has the same resolution it did before, and when I go back into my menu.lst file, everything is as it was before I edited it. Below are the changed I made (in bold).

Where should they go and what should they be instead?

EDIT: Also, can I delete the duplicate entries for Ubuntu and Recovery Mode below (in italic)?

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

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
**defoptions=vga=792 resume=/dev/hda2**
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

[I]title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot[/I]

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
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by veloce on 2007-02-25
From a quick look through, I note the following:

## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

Based on this, you need to alter the last line of this section:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

to include the options you want.

---

### Post by mgmiller on 2007-02-25
Here is where you made the change:  It is the wrong place.  You added it after the
end default options section.  Remove the line that you added.

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
**defoptions=vga=792 resume=/dev/hda2**  ***TAKE THIS LINE OUT***
savedefault
boot



Here is where you should put the line, it is higher up in the file:

> ## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash ** vga=792**



Do not delete any of the italic duplicate entries.  Do not edit anything below the line that says:
## ## End Default Options ##


After you have made the correct changes and saved the file, run:

```
sudo update-grub
```

You should then see the changes on the next boot.

The number you selected, 792 is for 1024 x 768 24 bit color.

---

### Post by 42Wired on 2007-02-26
Thanks. I was under the impression that # meant that line was a comment.

---

### Post by mgmiller on 2007-02-26
> Thanks. I was under the impression that # meant that line was a comment.

This is an area of contention noted by a lot of people.  Almost everywhere else in Gnome, a # would be a comment, but in this file, a double ## is a comment and a single # is an execute.  I don't know why this inconsistency exists.  Maybe it's some historical thing inherited from Unix, but that's just a guess based on nothing.

In any event, I hope everything went well and you now have a nice resolution for your boot screen.

---

### Post by 42Wired on 2007-02-27
So I'm not *that *crazy...

Yeah, it's perfect now. The console's resolution is much nicer, too.

---

### Post by 42Wired on 2007-04-24
Is there any way to make the resolution bigger in the boot manager? I ask because I get this "Out of Range" message in the middle of my monitor, and I want it to go away.

---

### Post by 42Wired on 2007-12-11
I just upgraded to 7.10, and now the steps in this thread don't seem to work to change the console's resolution.

---

