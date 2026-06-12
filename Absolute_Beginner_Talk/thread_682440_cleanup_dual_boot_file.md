---
title: "cleanup dual boot file"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Jbirdie1 on 2008-01-30
i have literally installed linux as a dual boot 10 times over the past 3 yrs...i never can find where the dual boot nfo is, so i can eliminate all refs to linux and not have to format!!! i do know that a dual boot of windows proggies writes the entries to the boot.ini file but i cant find the ubuntu stuff if i need to wipe it completely out...help and aloha

---

### Post by oedha on 2008-01-30
have you done this ?
sudo gedit /boot/grub/menu.lst

from this file you can set the default boot, timeout, title and so on

regards;
~E~

---

### Post by jaytek13 on 2008-01-30
> **Jbirdie1 said:**
> i have literally installed linux as a dual boot 10 times over the past 3 yrs...i never can find where the dual boot nfo is, so i can eliminate all refs to linux and not have to format!!! i do know that a dual boot of windows proggies writes the entries to the boot.ini file but i cant find the ubuntu stuff if i need to wipe it completely out...help and aloha

So, you've installed Linux dual-boot only to later decide you want to go back to windows, except when you remove Linux it leaves the boot partition intact, yes? 

The problem is that it writes these things to the 'boot' partition, which is the first partition on the primary hard drive, usually invisible to you, that sets up boot information. You would actually have to use a boot disk to fix the "corrupted" MBR and return it to normal. 

More information can be found at 

[http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prcb_dis_dgya.mspx?mfr=true](http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/prork/prcb_dis_dgya.mspx?mfr=true)


It's just the way things are. You cannot 'uninstall' ubuntu just as you can't 'uninstall' windows, so you'd have to do it this way to edit the MBR.


And just for an extra tidbit of information, the boot.ini file is -not- the boot partition. It is simply a file on windows that is referenced when the MBR is called.

---

### Post by Jbirdie1 on 2008-01-30
for whatever its worth...here is a copy of the current boot.ini file, there are usually 2 additional entries  - if ya install say win2k...then ya have an entry for win xp AND win2k and ya choose which ya want of there is a default at 30 seconds...since i saw it, then it must NOT be invisible:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by jaytek13 on 2008-01-30
> **Jbirdie1 said:**
> for whatever its worth...here is a copy of the current boot.ini file, there are usually 2 additional entries  - if ya install say win2k...then ya have an entry for win xp AND win2k and ya choose which ya want of there is a default at 30 seconds...since i saw it, then it must NOT be invisible:
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

As I said, the boot.ini file IS NOT the boot file. It is a file that is referenced by the MBR (master boot record) and nothing more.

I guess I'll add a bit more of an explanation here so you can understand what's happening:

Okay, so you have the MBR. The MBR references a boot record. Once you install Ubuntu, or most any Linux distro, the MBR is replaced with GRUB (or something similiar). This allows you to choose which OS to boot... I'm sure you already knew this.

Windows, however, does it differently. Windows will install their own version of GRUB into the MBR, except it references the boot.ini file. The default windows MBR will look at that boot.ini file for OS's instead of just giving you a selection. So, if I install windows, restart, the MBR comes up, the MBR will then look at the boot.ini file. If I have windows 2000 and xp installed, it gets that information from the boot.ini file, not the MBR. 

So, when you install GRUB, it references the boot.ini file also, NOT the MBR. So if I have 2000 and xp installed, grub will give me an option to boot windows, but upon that selection it will take me to another screen asking me if I want to load 2000 or xp... this is because it referenced the boot.ini file, and not the MBR.

---

### Post by Jbirdie1 on 2008-01-31
tks jaytech for your answer...lets get directly to the point...if i install ubuntu in a dual boot with windows (so i can send music and linux wont let me do that). but when i have installed ubuntu then i cant UNDO it, i am stuck with it or i must format my entire disk and reinstall windows again...is this correct??? there is absolutely NO way to uninstall/delete/wipe/linux out of a windows environment?

---

### Post by jaytek13 on 2008-01-31
> **Jbirdie1 said:**
> tks jaytech for your answer...lets get directly to the point...if i install ubuntu in a dual boot with windows (so i can send music and linux wont let me do that). but when i have installed ubuntu then i cant UNDO it, i am stuck with it or i must format my entire disk and reinstall windows again...is this correct??? there is absolutely NO way to uninstall/delete/wipe/linux out of a windows environment?

No. You'd just put in your windows install cd and boot to recovery mode which will take you to the command line. At the command line you would type

d://fdisk /mbr 

d being whatever letter your disc drive is, and then it will restore the MBR so that it takes GRUB off and puts the original windows MBR back on.

---

### Post by oedha on 2008-01-31
> **Jbirdie1 said:**
> tks jaytech for your answer...lets get directly to the point...if i install ubuntu in a dual boot with windows (so i can send music and linux wont let me do that). but when i have installed ubuntu then i cant UNDO it, i am stuck with it or i must format my entire disk and reinstall windows again...is this correct??? there is absolutely NO way to uninstall/delete/wipe/linux out of a windows environment?

wait.......calm down a bit........
what do you mean by so ican send music and linux wont ........ ?
if you stuck with ubuntu...you dont have to wipe entire harddisk....just use gparted...delete the ubuntu then recover your winblows with fixmbr and fixboot
your windows will be fine........

i am still using windows ( dual boot )....windows is only for my son and wife......
some of my friends were like you....they thought that they will stuck with ubuntu forever......no you wont.......and we will harm your windows !!

regards;
~E~

---

### Post by oedha on 2008-01-31
sorry...previously suppose to be ...we will not harm your windows..
thx~
~E~

---

### Post by sheki1 on 2008-01-31
I've installed Ubuntu 7.1 in a dual boot with Vista. However, I want to change the sequence so that it boots to Vista, not to Ubuntu by default. What do I need to change on my menu.lst file to do this?

The other option I could use is the one suggested in an earlier to post to run d://fidsk /mbr. However, I don't have Vista install CD, so how else could I execute this command?

Here's what my menu.lst shows:

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
# kopt=root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

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


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd0,3)
savedefault
makeactive
chainloader	+1

---

### Post by jaytek13 on 2008-01-31
Change "default 0" to "default 3"

---

### Post by sheki1 on 2008-01-31
changed default to 3 and got an error at boot time...

changed default to 4 and got the correct boot option.

Thanks!

---

### Post by Rome.konig on 2008-01-31
ok so you want to boot Vista before ubuntu on the menu list.  i copied your file and changed it to make Vista on top of the list. 


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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title Windows Vista/Longhorn (loader)
root (hd0,3)
savedefault
makeactive
chainloader +1


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
# kopt=root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=e8d3723d-bd87-4edf-9b5a-b08fd4bbae8a ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,1)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root




this should make your Vista on top of the boot list.  Just to be sure make a back up file for your /boot/grub/menu.lst

---

### Post by Rome.konig on 2008-01-31
woop nvm i didn't read the rest of this thread  sorry...:confused:

---

