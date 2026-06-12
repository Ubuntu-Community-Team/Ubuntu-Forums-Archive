---
title: "How does GRUB appear on screen at startup?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by kpfuser on 2007-05-25
Following an early unfortunate experience with GRUB and some painfully slow subsequent progress, I have reached the point where I need to ascertain how GRUB is supposed to appear on screen at startup assuming that it has been installed successfully (default installation) in a dual boot system (preferably by installing Ubuntu in a pc that also runs its initial Windows installation).

In my case, I get a GRUB prompt (grub> ) on screen at the outset, from where I need a workaround of sorts to go to the boot menu and then boot the OS of my choice manually as the default OS (Ubuntu) refuses to boot automatically regardless of how long I may wait.

Just recently, I managed to put GRUB on a floppy from where it boots into the boot menu (without the appearance of a grub> prompt) and 10 sec later boots Ubuntu automatically, if I fail to select a different OS in the meantime.

What I need to know is whether the way GRUB works when I run it from the floppy is the correct (default) way. How does GRUB work for the rest of you?

---

### Post by Hobo Joe on 2007-05-25
It just got installed with Ubuntu.....

I have no idea why you would need to use a floppy for that....
Maybe you should re-install.

---

### Post by bscbrit on 2007-05-25
The floppy way is the default on all of my systems.  Grub can be viewed, if it is hidden at boot time, by hitting the Esc key while the countdown is taking place.  If you post a copy of your /boot/grub/menu.lst that is resulting in the grub> prompt we can try and fix it for you.

---

### Post by bscbrit on 2007-05-25
I'm not sure a reinstall is necessary at this stage.  It might simply be a fault in you r /boot/grub/menu.lst file.  (In my opinion, the "reinstall first" is one of the wrong lessons learned from Windows.  It might be necessary but often faults can be cured by less drastic means. :-)  )

EDIT:  Correct spelling mistakes caused by typing too quickly and enjoying a relaxing beer at the start of my weekend!

---

### Post by Happy_Man on 2007-05-25
For me, GRUB starts straight up when it boots. As bscbrit said, if you post the output of 
```
cat /boot/grub/menu.lst
``` from a terminal, we can troubleshoot why your onboard version of GRUB gives you a prompt. And then you can use the floppy drive for other things!

---

### Post by dstew on 2007-05-25
Grub drops to the command line if it can find its root directory, but the menu.lst file is not there. At the grub> prompt, try **find /boot/grub/menu.lst** to see if grub can find some one somewhere. Of course, I am talking about the hard disk boot that gives you the problem. The floppy boot is using its own menu.lst file apparently.

---

### Post by kpfuser on 2007-05-25
Sorry for the delay! Bowing to popular demand, here it is, fresh out of the hard disk and not the floppy:

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

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

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
# kopt=root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,1)

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

title Ubuntu, kernel 2.6.20-15-generic
root (hd2,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd2,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a63a7fc9-5c59-4cb1-87d7-60bfddbf897d ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd2,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows 2000 Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

Awaiting developments!

---

### Post by kpfuser on 2007-05-25
> **dstew said:**
> Grub drops to the command line if it can find its root directory, but the menu.lst file is not there. At the grub> prompt, try **find /boot/grub/menu.lst** to see if grub can find some one somewhere. Of course, I am talking about the hard disk boot that gives you the problem. The floppy boot is using its own menu.lst file apparently.
It returns (hd2,1)

---

### Post by dstew on 2007-05-26
OK, try this. At the hard-disk boot grub command line, enter```
root (hd2,1)
setup (hd0,0)
```This should create a grub boot loader in the Master Boot Record of your first disk that will correctly find its root directory on your (hd2) disk. If the command fails, it might be because it wants the (hd0) disk to be unmounted. If that is the case, you can try to boot the grub floppy, and enter the same commands. If going the floppy route, get the command line by entering 'c', and check to make sure that if grub boots from the floppy it can find the root directory (hd2,1) by trying the **find /boot/grub/menu.lst** command again. It might return two answers, one for the floppy and one for the hard disk, but it might just return one if the floppy is using the menu from the hard disk also. If you get a different value from (hd2,1), then check back with the forum. If you get the same, go ahead and enter the **root** and **setup** commands to setup grub.

After you enter the setup command, enter **quit**, remove the floppy if you used it, and reboot. Hopefully you will get the menu.

---

### Post by kpfuser on 2007-05-28
Sorry for the delay. Back after a couple of days in picturesque but unconnected countryside.

To the point, I tried the commands
[B]root (hd2,1)
setup (hd0,0)[/B]
as instructed after booting first from the hd and, after this failed, from the fd, which failed as well. This is to say that after booting from the hd eventually, grub reverts to grub> and not to the hoped for menu of bootable OSs.

When booting from the fd, **find /boot/grub/menu.lst** returns
[B](fd0)
(hd2,1)[/B]

An observation made during these attempts: When grub loads from the hd, the first line that comes on screen is **GRUB: Loading stage 1.5**. However, when it loads from the fd, the same line reads **GRUB: Loading stage 2**. Is this of any relevance to the problem I have?

Question: Since the sequence
[B]root (hd2,1)
setup (hd0,0)[/B]
did not produce the hoped for result, would it be of any value to load grub from the fd and then try
[B]root (fd0)
setup (hd0,0)[/B]?

Another observation: When I enter **quit**, grub fails to recognize it as a command and reverts to grub>. When I hit **tab** to list all possible grub commands, I fail to see **quit** in the list as well as as anything else that would have the same effect, i.e., turn the pc off. Thus I am forced to stop the pc from the power switch.

---

### Post by dstew on 2007-05-29
I am sorry, but I made a mistake when I told you how to install grub. The commands should be```
root (hd2,1)
setup (hd0)
```
The command setup (hd0,0) will put the grub loader into the boot sector of the first partition of the first disk, not the master boot record (MBR). When you go to boot the hard disk, it is using the old grub in the MBR that is still there, and pointing nowhere apparently.

Your other questions: Stage 1.5 is really the same as stage 2, but in some cases grub installs stage 2 to the boot sector of a partition, and there it is called stage 1.5.

As to root (fd0), followed by setup (hd0), that will work, but you will need to have the floppy disk in every time you boot the system, in order to read the menu.lst file.

About the quit command, it only works when you are using the grub shell. This is when you are running grub under a running operating system, like when you boot a live CD, and then invoke grub. When you run grub from an install like you are doing, there is no running operating system to go back to, hence no quit command. I am sorry I led you astray by this mistake also. When you finish the installation commands, enter the command **reboot**.

One last thing. It is possible the command setup (hd0,0) overwrote part of the Windows boot loader. If you find that you cannot boot Windows, you can fix this by the Recovery Console command **fixboot** (not fixmbr).

---

### Post by kpfuser on 2007-05-31
Well, after another short absence I am back to my continuing grub problems.

Sorry to report that trying
[B]root (hd2,1)
setup (hd0)[/B]
after booting from the hd first to the familiar grub> and then from the fd to grub> after hitting 'c,' not only did not solve the problem but it made it worse. Now if I boot from the hd to grub> as before, when I try my old workaround of hitting 'tab' first and then 'esc' twice produces a menu where the former two first entries, i.e., booting Ubuntu 'Generic' and Ubuntu 'Recovery Mode' are repeated. If I try to boot Ubuntu 'Generic' from the first entry, the system starts ok but after a short period it hangs. Booting from the second Ubuntu 'Generic' entry or from the fd succeeds as earlier.

So what can I do from this point? Am I loading my hds with conflicting entries? How can I delete the two new (repeated) entries from the boot options list? And most of all how can I enter the info that will allow grub to run normally from my hd?

---

### Post by dstew on 2007-06-04
Hi, I am also back from a short trip. There are two separate problems here. First, when you boot grub from a hard disk, it gives you a prompt instead of a menu. Second, the menu you get with your keystroke input is messed up.

I need to understand why your system is behaving as it is. Let's focus on the hard disk boot. When you turn on your computer, you get a simple grub prompt, correct? What I don't understand is why you hit tab and esc twice. From my understanding of grub, if you hit tab at the command prompt you get a list of commands. The tab key works to complete partial commands, like it does in linux. For me, esc just clears the screen.

---

### Post by kpfuser on 2007-06-04
You got everything right. Just add one more problem to the list, i.e., Win2k fails to boot after the last attempt to correct the GRUB problem. I have no idea why the sequence tab followed by esc-esc brings up the menu. However, this is of little help now as the menu is messed up and Win2k fails to boot. I have decided to reinstall everything from scratch. Since I am going to delete everything on all hds, I will not be able to implement any further remedies you suggest. Thanks for all of your suggestions and too bad this story did not have a happy ending. At least I managed to learn quite a few things about the inner workings of GRUB.

---

### Post by dstew on 2007-06-04
OK, good luck. I am trying to learn too, that's why I like to keep trying.

---

