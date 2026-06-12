---
title: "My Computer Is Freezing!!"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by borovy3488 on 2007-08-18
So far, everything has been going excellent in Ubuntu.  I only have one problem.  Every time I leave my computer (i dont log out or anything, it just sits on the home screen and the monitor goes black) idle for more than an hour or two, when I come back, it freezes.  Like, I will move the mouse, and the screen will come back, but nothing will work.  My mouse moves, but thats all.  Has anyone else had this problem??  I'm using a Gateway M520HX laptop.  

Thanks,
Wayne

---

### Post by scrooge_74 on 2007-08-18
Change the settings for suspend and hibernate for a longer time period.  Then you need to research in which way it manages hibernate.

Check if [this]("http://ubuntuforums.org/showthread.php?t=237264&highlight=suspend+hibernate+howto") helps.

---

### Post by borovy3488 on 2007-08-22
Thanks for the help.  I tried the mothod above, with no success.  On boot, I got like 3 error messages, but they disappear so fast I can't see them.  Then the system boots up as normal, but it is all VERY slow.  Plus, now my volume buttons dont work.  I just erased all of those steps.  Any other suggestions??

Thanks,
Wayne

---

### Post by Jimmyfj on 2007-08-22
Have you checked the screen saver settings? I've had problems returning from blank screen when my screen saver wasn't set - All I could do was restart X and then all worked fine.

---

### Post by sawjew on 2007-08-22
There seems to be a consistent problem with Feisty with freezing.  I have had the problem and resolved it by adding "noapic" to the boot parameters.  To do this you need to edit the grub boot loader menu list.  To access the menu list open a terminal and type ```
sudo gedit /boot/grub/menu.lst
```

this will open a file which looks like this
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
# kopt=root=UUID=9f0b3566-30ac-46e8-963d-85e1281534c1 ro

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
# defoptions=splash [COLOR="Red"]noapic[/COLOR] vga=791

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9f0b3566-30ac-46e8-963d-85e1281534c1 ro splash noapic vga=791
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=9f0b3566-30ac-46e8-963d-85e1281534c1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

The important line is this one
```
# defoptions=splash [COLOR="Red"]noapic[/COLOR] vga=791

```

After you have added this line and saved and closed the menu list you need to enter in the terminal
```
sudo update-grub
```

This will add the parameter to all your kernels listed in the menu list.

Don't worry about the other parameters but this may fix the problem, it did for me.

If you still have problems search the forums for "noapic", "nolapic" and "acpi=no" and see if they help.  You can add all sorts of parameters to the defoptions in grub to fix problems but you should avoid the "acpi=no" if you can because this will disable all your power management options.

Good luck.

---

### Post by zero244 on 2007-08-22
The noapic loapic fix could fix the freeze, from the above post.
Also make sure you dont have a 3d screen saver enabled unless you have 3D drivers.
For your screen going blank whether you have your monitor set for power down or not.
There is a bug in Edgy and Feisty that causes that.
To stop your monitor from powering down, put this section on the end of your xorg.conf file.

Section "ServerFlags"
Option "blank time" "0"
Option "standby time" "0"
Option "suspend time" "0"
Option "off time" "0"
EndSection

This is the only way I could stop my monitor from powering down after ten minutes in Edgy and Feisty.

---

### Post by borovy3488 on 2007-08-23
Wow, I think I have tried everything.  All of the resolutions above and any other ones I could find.  Still nothing.  Here is EXACTLY what is happening.  If I either lock the screen or just let it sit for more than 2 hours, on startup nothing happens.  I can't do ANYTHING.  For the first, maybe 3 seconds, like I can roll over avant window navigator and it will start coming up, but then EVERYTHING stops.  Nothing will work.  I did try to ctrl+alt+backspace.  It woked once, but everything was really slow.  It seems like the only way to fix it is a restart.  Does anyone have any more ideas??  As of now, this is the only thing that is making me wonder if i should go back to windows.  Other than this Ubuntu is AWESOME, but I would never make it without this forum.  You guys are awesome.  :guitar:

Thanks in advance

---

### Post by borovy3488 on 2007-08-23
any more ideas out there??

---

### Post by borovy3488 on 2007-08-24
Hump de *BUMP* doop bodu
*BUMP* de hump doop bop
Hump de *BUMP* doop bodu

-RHCP

---

### Post by scrooge_74 on 2007-08-24
Wrong thread, the extra Bumps go in [here]("http://ubuntuforums.org/showthread.php?t=520091")
Sorry ran out of ideas to help you :)

---

### Post by sunspots on 2007-08-29
I have been testing Gutsy Gibbon Tribe-5 and found the sleep to work but not the hibernate. Actually, it hibernates but I can't revive the system from hibernation.

Have a look at the following bug report.
[https://bugs.launchpad.net/ubuntu/+bug/135088](https://bugs.launchpad.net/ubuntu/+bug/135088)

It would be good if you applied your comments to it. It is unlikely that it will be fixed on anything before Gutsy. I had similar comments on another problem I found, but they fixed it for Gutsy Tribe-5.

If you can spare some time and test Gutsy it would be great and reporting bugs in the latest flavour will help us all.

Sorry I can't offer much else.

---

