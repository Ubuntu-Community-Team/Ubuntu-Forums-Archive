---
title: "Init 3 not launching!"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by gezus on 2007-03-04
Hello All.
I can log into run level 5 very smoothly no issues and have even updated my ATI drivers.
However if I type in "sudo init 3" or "sudo telinit 3" nothing happens.

If I type in "sudo telinit 1" to drop to single user mode.  The non graphical interface does appear, but the screen is flickering constantly and can barely see the prompt to know what I am typing in.

I am very new to Linux and have no idea what might be causing this problem at all, if anyone can offer assistance please do.

Best Regards,

Sean.

---

### Post by taurus on 2007-03-04
What are you trying to do?

---

### Post by Mr. C. on 2007-03-04
This was a way to change runlevels in traditional System V Unix systems.  It appears that the Ubuntu graphical environment does not want to be shutdown this abruptly, and init N/telinit N apparently has been disabled.

[ EDIT:  my analysis was incorrect.  Ubuntu has the graphical environment configure for run level's 2-5.  This is why telinit and init appear to not succeed.  Run levels are changed, as one would expect, but the GDM environment is configured to shutdown and be replaced by a console-only shell. ]

MrC

---

### Post by gezus on 2007-03-05
Odd, because like i said if I type in init 1 it works just init 3 is not working.

Does anyone know how to change it to allow init 3 from init 5.

---

### Post by macogw on 2007-03-05
well you can drop to a tty wih ctrl alt f1, then do 
sudo /etc/init.d/gdm stop
to kill X completely

---

### Post by gezus on 2007-03-05
and i think this is part of my problem.

ctrl alt f1 drops to a tty, but again i experience the flashing screens and can barely see the prompt.

I have not tried sudo /etc/init.d/gdm stop while this flashing occurs to see if killing X would fix it.

But I just cannot seem to wrap my head around the flashing screen.

---

### Post by taurus on 2007-03-05
What exactly are you trying to do?  Are you trying to install a driver for your graphic card or something?

---

### Post by gezus on 2007-03-05
Taurus,

Sorry no I am not trying to do anything in particular, I am just messing around with Linux in general and noticed it wasn't working so figured i'd bring it up, to see if there is a way to drop to init 3 from the graphical interface, and also if anyone might have any insight as to the flashing screens.

---

### Post by taurus on 2007-03-05
If you want to stop gdm/kdm, you either have to kill it or remove it from /etc/init.d!  

And regarding the flash screen while you are in a console, can you post your /boot/grub/menu.lst here?

```
cat /boot/grub/menu.lst
```

---

### Post by gezus on 2007-03-05
Taurus, I definitely will do that.  
I did not install SSH and am at work so will get it later tonight when I am at home.

Thanks,
Sean.

---

### Post by Mr. C. on 2007-03-05
Please see my Edit above.  My explanation was in error, and has now been corrected.

Sorry for the mis-information.

MrC

---

### Post by steve.horsley on 2007-03-05
gezus: As Mr. C has said, Ubuntu is configured for X (the GUI) to be running in runlevels 2-6, so changing between those runlevels will not make any difference. To stop X, use the command:
**sudo /etc/init.d/gdm stop**

Red Hat based distos normally boot into runlevel 5 and have runlevel3 set for no GUI. Ubuntu / Debian defaults to runlevel 2 with all runlevels esentially the same. This is of course configurable.

---

### Post by gezus on 2007-03-05
Taurus as promised, here you go.
I understand the reasons now around init.  My problem though is now merely with the flashing I am getting when I push CTRL+ALT+F1 (flashing occurs) and when I push CTRL+ALT+F7(no flashing, everything fine).

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
# kopt=root=UUID=14acc37b-073e-439d-aaac-57fa122f4984 ro
# kopt_2_6=root=/dev/hda1 ro

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by taurus on 2007-03-05
Try to add "vga=773" to your kernel entry in /boot/grub/menu.lst 

```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda1 ro **vga=773** quiet splash 
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

```
and see if the flashing screen goes away when you are in a console.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by gezus on 2007-03-05
Dang!
Didn't work :(

Pretty sure I didn't have to reboot after I made that change.

---

### Post by taurus on 2007-03-05
Actually, you need to reboot after you made that addition to /boot/grub/menu.lst.  And I assume you are using that kernel, then one that you added vga=773 to.

---

### Post by gezus on 2007-03-05
Sweet that definitely stopped the flashing!!

Now every line is missing a few characters on the left.  I assume that to fix that I just play with that 773 number?

In any case, thank you very much for your expertise.  It's greatly appreciated.

---

### Post by taurus on 2007-03-06
Change the vga=773 to vga=791 and you would be able to view the whole screen then.

---

### Post by tubasoldier on 2007-03-06
This is one thing that drives me nuts about Ubuntu. I too have used the init run levels on all other linux distros. Ubuntu makes no difference between run level 2-5. yuck! Completely configurable but also a complete pain in the rear.

---

### Post by gezus on 2007-03-06
Interesting, even after changing vga=773 to vga=791 I can still not see the left most characters.
The only way I can do that is if I use the monitor adjustment to move the screen to the right.

Is there a way, and again I apologize for my ignorance to the subject, to control the size of the screen when seen in ctrl+alt+f1?

---

### Post by gezus on 2007-03-07
Just refreshing this in case someone knows how to resize the screen seen in ctrl+alt+F1.

---

### Post by Mr. C. on 2007-03-07
> **gezus said:**
> Interesting, even after changing vga=773 to vga=791 I can still not see the left most characters.
The only way I can do that is if I use the monitor adjustment to move the screen to the right.

Is there a way, and again I apologize for my ignorance to the subject, to control the size of the screen when seen in ctrl+alt+f1?

This problem is common with monitors that support multiple frequencies, resolutions, and sizes.  Some monitors have NVRAM so that your changes for a given resolution are retained on power down.  Some do not.

I don't know if there is any screen shifting or adjusting utility.

MrC

---

### Post by gezus on 2007-03-07
> **Mr. C. said:**
> This problem is common with monitors that support multiple frequencies, resolutions, and sizes.  Some monitors have NVRAM so that your changes for a given resolution are retained on power down.  Some do not.

I don't know if there is any screen shifting or adjusting utility.

MrC


Oh well I guess,

Thank you though for the help.
I wonder if this might be attributed to the fact that I am using a KVM.

In any case, thank you kindly.

---

### Post by Mr. C. on 2007-03-07
> **gezus said:**
> .
I wonder if this might be attributed to the fact that I am using a KVM.

Yes!  This will affect the signals the monitor senses; how well the KVM maintains the signals, and what it presents to the monitor depends on the quality of the KVM.  Cheap KVM switches are problematic in such areas.

MrC

---

### Post by steve.horsley on 2007-03-07
I have found that when using a KVM, X cannot figure out what screen you have, and it defaults back to a safe 640x480. You can overcome this by specifying the horizontal and vertical monitor frequency ranges by hand. 
Here is an extract from my copnfig file /etc/X11/xorg.conf. Don't change anything except the frequencies (you can add them if they're not there):
```
Section "Monitor"
	Identifier	"E-171"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection
```

always back this file up before editing it.

You can also edit it with this command:
**sudo dpkg-reconfigure xserver-xorg**
(that;s how I found my refresh rates - I let it autoconfigure them).

---

### Post by Mr. C. on 2007-03-07
Be SURE to use your own monitors timing specs; you *can* damage your monitor with inappropriately high rates.

MrC

---

### Post by steve.horsley on 2007-03-07
> **Mr. C. said:**
> Be SURE to use your own monitors timing specs; you *can* damage your monitor with inappropriately high rates.

MrC

Abso-bleedin'-lutely! 
My monitor is an LCD one, so it has a very wide sync range compared to a lot of CRT monitors. Those numbers above are NOT suitable for CRTs.

---

### Post by Linuturk on 2007-03-12
> **steve.horsley said:**
> gezus: As Mr. C has said, Ubuntu is configured for X (the GUI) to be running in runlevels 2-6, so changing between those runlevels will not make any difference. To stop X, use the command:
**sudo /etc/init.d/gdm stop**

Red Hat based distos normally boot into runlevel 5 and have runlevel3 set for no GUI. Ubuntu / Debian defaults to runlevel 2 with all runlevels esentially the same. This is of course configurable.

What is the point of having different run levels if they aren't used for anything?

---

### Post by Mr. C. on 2007-03-12
> **Linuturk said:**
> What is the point of having different run levels if they aren't used for anything?

They are used by other distros, they were used for configurations that are less valid today.  When this stuff was developed, not every system had a network.  It was a generalized startup mechanism that provide forward thinking, which ended up only needing a few states.

Consider if you are a gamer, and want your run-level 5 to be the full GUI, and all the services you run.  But you could easily configure run level 3 to be a leaner configuration; going back and forth between run levels is trivial.

MrC

---

