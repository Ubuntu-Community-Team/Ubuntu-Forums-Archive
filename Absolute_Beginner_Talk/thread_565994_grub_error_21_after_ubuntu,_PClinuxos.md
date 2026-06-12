---
title: "grub error 21 after ubuntu, PClinuxos"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by adamm07 on 2007-10-02
ok, new guy here, taking a linux class at the community college and i am now obsessed with Linux lol.

i have searched everywhere, but here it goes.

ok, i had vista on my pc at first. Well, i did a step-by-step process of shrinking partition on vista, installed ubuntu, and of course it screwed up (my luck huh). 

Well thats when things got screwy. Ubuntu wouldnt boot up, and i would get the GRUB error 21 after it says "grub loading stage 1.5, grub loading, please wait..... error 21"

Now i've read that is the grub not detecting a hard drive. I go into my bios and see that it has detected my hard drive....

so i try to get PCLinuxOS to work, run the live cd and i format the hard drive and run a 20gb ext3 and a 2gb swap (only 1gb ddr2 ram :( ) Well i restart after the "install" which takes like 5 minutes, seems way too short. 

I reboot, and there it is, the grub 21 error again. It did basically NOTHING to the hard drive....

ive also read that it could be my MBR (master boot record i'm assuming?)


If anyone can help me, that would be great, i love linux too much to give up.

keep in mind i'm not a command freak so the terminal is still quite new to me, so newbie layout please lol.

---

### Post by sirgogo on 2007-10-02
Much "lol"'s to you too my friend.

Concerning your issue: From my experience of installing Ubuntu, I have found that this may be a problem with you graphics card. I tried, (and failed) , to install Ubuntu on a P4, GeForce FX 5200 graphics card with 1 GB ram, things got screwy because the graphics card was an ancient version and wouldn't work. The installed worked 1/2 the time, (I finally installed it), but then wasn't able to boot.

Unfortunately for you, you will have to get a text based installer and use Ubuntu from the terminal-- whereby you can download your graphics drivres (if that IS the problem) and then install a GUI.

I could be wrong though, so good luck, and tell me how it goes.

---

### Post by adamm07 on 2007-10-02
thanks^, i'll hopefully get it soon.

forgot to mention specs

Intel Core 2 2.4ghz, 1gb ddr2 ram, 250gb in PATA (stupid WD cheap hd) asus p5b deluxe board, GeForce 7600 gs gfx card.

i do remember i have to run pclinuxos in vesa mode, but not Ubuntu.

i dont believe its my video card, it something dealing with hard drive.

it wont let the partitions be created.

---

### Post by mridkash on 2007-10-03
I think this same problem occurred with my friend's laptop where Windows installer couldn't find a hard disk in the laptop and BIOS listed it there.

I dont know how he resolved it, I think he gave his laptop to company for repairs.

---

### Post by adamm07 on 2007-10-03
well im going to try a different hard drive and see how it goes.

its hard for me to send it in for repairs when all of my pc's are custom.

but if the other hard drive works, what does that mean about the other one? it can no longer write, it may be fried?

---

### Post by dpar on 2007-10-03
Can you boot into Vista?

---

### Post by dpar on 2007-10-03
Ok, after a little search, I found this , which may be relevent.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by adamm07 on 2007-10-09
ok, i know its something to do with my grub/mbr.

can anyone tell me if my grub menu.lst file is good?

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
default		0

gfxmenu=/etc/grub/message.mint

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/sda2 ro

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

## ## End Default Options ##

title		Linux Mint, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Linux Mint, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.20-15-generic
boot

title		Linux Mint, kernel memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by alienexplorers on 2007-10-09
Did you try reloading Grub from the Live-CD.  I have a link in my sig explaining how to do this.
Your Grub Error 21 means:
21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.

---

### Post by eph1973 on 2007-10-09
In your menu.lst you might try to comment out the section about gfxmenu=/etc/grub/message.mint.  Just put a # in front of it so that it reads:
```
# gfxmenu=/etc/grub/message.mint
```

This is unlikely causing your problem, but try commenting it out, just until that A) you resolve your issue with your GRUB error and B) you verify the existence of the file /etc/grub/message.mint (if you type ls /etc/grub/message.mint, you do not get the response ls: /etc/grub/message.mint: No such file or directory)

Other than that, it looks fine.

You should download and burn the .iso file available [here]("http://supergrub.forjamari.linex.org/"), and try that to fix your problem.

---

