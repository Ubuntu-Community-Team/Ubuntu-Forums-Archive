---
title: "[SOLVED] SH*T! deleted vista recovery now it won't load all i wanted was more space f"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by S15_88 on 2007-07-22
So i've got ubuntu dual booted with vista for a while now and i wanted more disk space in ubuntu so i decided to delete the 10GB recovery partition, from vista of course, and then i booted into ubuntu a buch of times then i needed to go into vista and i get Error 12: invalid device requested
i read online that it is safe to delete this partition for extra space and the IT guys at my work said go for it!  wat happened!!!!!!!!!!!!!!!!!!!!! please help!!!!!!!!!!!

thanks, Alain

if anyone needs specs of command line output let me know and i'll post it!

---

### Post by buntunub on 2007-07-22
:popcorn:

:lolflag:

OMG thats too funny!

Anyway, Congratz on that. Now you can make the switch to linux like it or not.

---

### Post by BETOCORELLA on 2007-07-22
Same Problem Here. Dam Ubuntu Installed N All I Get Is A Black Screen. Vista Got Erased

---

### Post by wolfen69 on 2007-07-22
deleting recovery partition will not cause this issue.

---

### Post by S15_88 on 2007-07-22
well i'm happy in linux i have my wifi working and everything that's why i wanted the extra space but before i deleted the recovery partition i could dual boot perfectly fine!  i'm jus wondering if i could wipe vista right off and then  reinstall in and see what will happen?

---

### Post by meierfra on 2007-07-22
I would guess that the names of your partitions have changed and grub  is  trying to boot into the wrong place.
Post the output of

sudo fdisk -l

and 

sudo gedit  /boot/grub/menu.lst

---

### Post by starcraft.man on 2007-07-22
> **S15_88 said:**
> So i've got ubuntu dual booted with vista for a while now and i wanted more disk space in ubuntu so i decided to delete the 10GB recovery partition, from vista of course, and then i booted into ubuntu a buch of times then i needed to go into vista and i get Error 12: invalid device requested
i read online that it is safe to delete this partition for extra space and the IT guys at my work said go for it!  wat happened!!!!!!!!!!!!!!!!!!!!! please help!!!!!!!!!!!

thanks, Alain

if anyone needs specs of command line output let me know and i'll post it!

Firstly, what IT guys on this planet would tell you to delete recovery partitions? You did create fully functioning recovery CDs first right? Or at least image the partition/OS installs? Once it's gone that's it, less you stop writing to the disk right now and reconstruct the partition somehow. That's your media for reinstalling your OS, without it I hope you never have need to reinstall that copy of Windows again.

As for the error, I dunno what Vista could possibly need from a recovery partition.

Oh and hi fellow Canadian, I love seeing more of us around :D.

---

### Post by buntunub on 2007-07-22
Ubuntu will not screw with your windows install unless you mess something up either accidentally or purposefully. In fact the Buntus even have a windows based install (Wubi) that will live in tandem. I can tell you from experience that Fedora WILL. I can also tell you that if your dealing with HP, your SOL if you wipe your recovery partition. They do not provide backup CD's and are very unforgiving if you screw up the recovery partition. They WILL send recovery CD's (after you talk to thier Indian or Sri Lankan guy on the phone for an hour) but they will charge you for it. They sent me 2 sets of recovery CD's and none of them worked. Wolfen is right however, wiping the recovery partition will not screw up your windows base install. You must have done something to screw with that as well. My advice, just do what I did and say buh bye to M$. Im seriously not regretting that decision one bit.

---

### Post by S15_88 on 2007-07-22
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *        1312        6400    40868261+   7  HPFS/NTFS
/dev/sda3            6401       19457   104880352+   5  Extended
/dev/sda5            6401       17998    93160903+  83  Linux
/dev/sda6           17999       19261    10145016   83  Linux
/dev/sda7           19262       19457     1574338+  82  Linux swap / Solaris


> 

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
# kopt=root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro irqpoll
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ab5a2558-1345-48e9-bb01-833b499f021a ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1



as for the IT guy it's actually Head of IT of our company and he said as long as i have the vista CD it's fine because he guessed i wouldn't be doing crucial things in vista that i would ever need to recover sumthin.  

thanks, for the help!

---

### Post by meierfra on 2007-07-22
Just a guess. But maybe all you have to do is change

root (hd0,2) 

to 

root (hd0,1) 

 in the windows section at the end of the file /boot/grub/menu/lst

---

### Post by meierfra on 2007-07-22
I posted my last message before I saw your output. Now I'm pretty sure that that is all you need to do. Let me know if you need more detailed instructions.

---

### Post by SPQQKY on 2007-07-22
> **buntunub said:**
> :popcorn:

:lolflag:

OMG thats too funny!

Anyway, Congratz on that. Now you can make the switch to linux like it or not.

Real nice.The guy was looking for help and all you can do is laugh and mock. Stay away from these forums as your only purpose is to serve as a bad example.

---

### Post by S15_88 on 2007-07-22
ya i panic'd haha all i had to do was stop and think i realized that i had to make the switch there after i posted the output for you and looked at it! everythings fine now haha close call, got me scared for a second.  thnks for the help everyone!

---

### Post by HermanAB on 2007-07-22
Actually, virtualization has matured nicely in the last year or two.  You could reclaim all the disk space for Linux and run XP or Vista under VMware Server, Qemu or VirtualBox when you need to.  It is far nicer to have Windows running in a window, concurrently with your Linux applications, than having to reboot.

---

