---
title: "[SOLVED] Dual boot problems and further Windows error."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by rorymcv on 2008-02-12
I've installed windows xp after installing ubuntu (7.10) but am having problems getting Windows to boot. Sorry for being a clueless noob - I've spent hours trying to find a solution on the forums without having to resort to seeking help but I'm sure someone out there can solve this in a matter of minutes.   

I've gone through the process at [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

The problem is where I specify the root to load xp from. I've entered...

"root (hd0,1)"   all the way up to "root (hd0,5)" but keep getting error messages - so the first thing I need to know is which value to use here. Here's my 'sudo gedit /boot/grub/menu.lst'  (not sure if this helps but I am very new to this!)


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

Some more info which you might need is that GParted shows my XP partition as /dev/sda1 and Flags show this as 'boot'.  Ubuntu is /dev/sda2.

When grub loads, Xp is the 4th option, but I always get an error message when I select it.


Secondly - I've used Supergrub to attempt to boot XP - it initially appears to boot, but then I get a chksum error followed by a blue screen. So I imagine that even if I did get grub to find windows - I would still get this error. Any suggestions???

This is my first post and I imagine this is an incredibly common problem so apologies for giving you deja-vu but I've been stuck at this for 3 days now and would like to move on. Overall I'm really impressed by Ubuntu - I never thought it would be as user friendly as it is and (pardon me for being shallow here...) its just so much prettier than windows!! The only reason I'm keeping windows is for itunes and some games.
Thanks in advance for any help you can offer - let me know if you need some more info printed.

---

### Post by mrsteveman1 on 2008-02-12
Your windows partition is (hd0,0)

so the grub entry is as follows:

Title Windows
rootnoverify (hd0,0)
chainloader +1

Try that before you try anything else.

If that doesn't boot the windows partition there are other things that can fix this easily.

---

### Post by rorymcv on 2008-02-12
Hi Steve

Thanks for your quick reply.
I've tried your suggestion but now the option to boot Windows has disappeared from my grub choices menu so I'm still stuck.

---

### Post by mrsteveman1 on 2008-02-12
So you can boot into linux right?

If so, is there still a windows entry in /etc/menu.lst? If the entry is there you should be able to see it when you boot.

---

### Post by rorymcv on 2008-02-13
Hi again

Yes - I can still boot ubuntu without any problems.
The windows entry is still on the list - I've entered exactly what you've told me but its not showing as a boot option.  Here's the list...


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

Title 		Windows
rootnoverify 	(hd0,0)
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST

Any ideas???

---

### Post by mrsteveman1 on 2008-02-13
So as far as i can see, the issue is that grub isn't paying attention to the /boot/grub/menu.lst file for some reason.

One thing i do notice, the windows entry shouldnt be inside the "automagic kernels list" because it will get removed by ubuntu with updates. So move that below the automagic area and see if that helps.

There might also be another setting in the menu.lst file keeping the windows entry from showing up as well.

---

### Post by rorymcv on 2008-02-13
Okay - I've moved the windows entry down but still no joy on booting. Here's my complete list ...

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
timeout		4

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)


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
# kopt=root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


Title 		Windows
rootnoverify 	(hd0,0)
chainloader +1




Let me know if there's anything else I can print to help.

---

### Post by mrsteveman1 on 2008-02-13
So when you boot you see the following 3 options on the grub screen?

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+


It might be worth a try to do the following:

start the system, when grub comes up press esc, then C (might be slightly different)
type rootnoverify (hd0,0)
then chainloader +1
then boot

what happens?

---

### Post by rorymcv on 2008-02-13
Now we're getting somewhere....

All good - my menu is just as you described. I input your commands and XP loaded without any 
problems - not even with the error messages I was getting when I used supergrub. Splendid.

The problem's obviously to do with my system not paying attention to the '...menu.lst' document when booting.  I had a similar problem a couple of days ago. Grub would try to load ubuntu from hd (0,2) - changing the entry in the '....menu.lst' file to hd (0,1) didn't fix the problem, though I could load ubuntu by pressing 'e' on boot and changing the instruction there.  Now if only I could remember how I fixed that problem we'll have cracked it..... (my memory's not the greatest after a couple of glasses of wine!)  Any ideas?

Thanks a bunch for your help - much appreciated.

---

### Post by Razorback on 2008-02-13
## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e1bb6fe6-33cd-4cd4-8a23-c979a8e88ab6 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

[COLOR="Red"]
Title Windows
rootnoverify (hd0,0)
chainloader +1[/COLOR]

### END DEBIAN AUTOMAGIC KERNELS LIST



You need to  have your windows selection inside the list to be able to see it in your list.

---

### Post by rorymcv on 2008-02-13
EUREKA!!! I've cracked it!  Here's what happened...

I took Razorback's advice and moved the windows title back to where it originally was and rebooted. No luck - it still wasn't an option. I had another look at the '...menu.lst' file and realised something.  Wait for it ... the Windows instruction has the word 'title' spelt with a capital 'T'.  I changed that, rebooted and hey ... everything's now on my menu and I can now load any OS I like.  

I then experimented and moved the windows part back to where Mrsteveman1 originally told me (so that it doesn't get removed when ubuntu updates), rebooted and hey presto - Windows is still an option on boot and everything seems to be working well. :)

Thanks for your assistance ... now I can finally move on and tackle some other little projects.

---

### Post by mrsteveman1 on 2008-02-13
Glad it works now :D

---

