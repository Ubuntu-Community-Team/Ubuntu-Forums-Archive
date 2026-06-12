---
title: "windows won't boot T_T plz help!"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by chdragonfly on 2007-05-20
I just installed the ubuntu Feisty Fawn 7.04 and everything on the ubuntu side works. when i tried to boot into windows, it just shows a blank screen and does nothing.  Is this fixable and how? The system recovery works. 

thanks.

EDIT!!!
my windows is booting again! w00t!!! I used the windows xp cd and did chkdisk..and then it just work. o.O 
thanks to everyone that tried to help!! :)

---

### Post by ~SkyBlue~ on 2007-05-20
My guess is there's a problem with your bootloader. Try boot from ubuntu alternate cd and select 'rescue' to edit your bootloader, I'm not too sure how but if you search around the forum there are some good tutorial on it.

---

### Post by chdragonfly on 2007-05-20
ok, I'm downloading the alternate cd right now. 

This is how I partitioned the drives...hope it helps? [IMG]http://img237.imageshack.us/img237/9451/gpartedzs8.jpg[/IMG]

this is what I get when I run the grub menu/script? 
[SIZE="2"]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=0d4312f1-3ec3-48d5-b2b9-9b65d8433787 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0d4312f1-3ec3-48d5-b2b9-9b65d8433787 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=0d4312f1-3ec3-48d5-b2b9-9b65d8433787 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows NT/2000/XP
root		(hd0,1)
savedefault
makeactive
chainloader	+1
[/SIZE]

Is this problem fixable? or am I just doomed? 
thanks for any help!

---

### Post by drowner on 2007-05-20
GRUB seems to have found windows installed TWICE on your computer. Is this correct?

---

### Post by chdragonfly on 2007-05-20
I don't understand what you mean?

---

### Post by drowner on 2007-05-20
If you look at GRUB's menu.lst, it mentions that you have ONE windows installed on your large NTFS partition (sda1)  and another windows installed on your small fat32 partition.

Is this correct? Do you have windows installed twice on your computer?

---

### Post by chdragonfly on 2007-05-20
No, the smaller partition only contains System Recovery. Like when i boot using that one, it only have 2 options, 1 is destructive recovery and the other full system recovery with backup. Only the partition on NTFS have windows or should.

---

### Post by drowner on 2007-05-20
Oh I see.

I'm not entirely sure what the problem is then. The menu.lst looks right to me.... does everyone else agree?

---

### Post by chdragonfly on 2007-05-20
here's what my boot.ini looks like
>  [boot loader]

timeout=5

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /noguiboot

im just trying diff things as ppl suggest them and posting results here in hope that it will help?

---

### Post by ugm6hr on 2007-05-20
Couple of thoughts...

I agree with drowner - can't see any major issues with GRUB's menu.lst that you posted.

As for Boot.ini - in order of likely help (try 1 at a time): 
Presumably the space in "WINDOW_S" on line 3 was an issue with cut & paste?  If not - that should be corrected (and is the obvious problem).
Might be worth deleting the "/noguiboot" on line 5 - at least then you should get the "Windows XP loading" screen - it might give you a clue as to where the problem is.
Other potential adjustments to line 5 include /safeboot or /bootlog - details given in [http://www.microsoft.com/technet/sysinternals/information/bootini.mspx](http://www.microsoft.com/technet/sysinternals/information/bootini.mspx)
The other thing that occurs to me is: has Gparted changed the partition labels? If so, it might be worth trying to change "partition(1)" to "partition(2)" on lines 3 and 5.

Hope you manage to sort it out.  Otherwise - you could use Ubuntu to back-up all your important files (you should be able to find all your email / internet / personal setting files with a bit of work) on the XP partition, and then use the recovery partition to re-install XP (as per factory original).  Obviously you'd have to re-install all your Windows applications and settings.  I was doing that every year with Windows anyway, which is why I moved to Linux!

---

### Post by chdragonfly on 2007-05-20
It wouldn't let me make changes to boot.ini since its in the windows part of the partition. How can I change the boot.ini?

---

### Post by chdragonfly on 2007-05-20
bump T_T

---

### Post by ugm6hr on 2007-05-20
in a terminal - try entering:
gksudo nautilus

then find boot.ini, save a copy somewhere, in case you make a mess of it, and then edit it as you want.  remember to save it as a plain text file again.

PS: I use Xubuntu, so it's "gksudo thunar" for me - but I think Ubuntu proper uses nautilus.

**EDIT: Had another idea to try and ascertain where the problem is:**
Edit boot.ini, and add extra lines at the bottom with the following (just cut and paste):
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP1 GUI" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP1 Bootlog" /noexecute=optin /fastdetect /bootlog
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP1 Safeboot Network" /noexecute=optin /fastdetect /safeboot:network
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP1 Safeboot Minimal" /noexecute=optin /fastdetect /safeboot:minimal
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP2 GUI" /noexecute=optin /fastdetect
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP2 Bootlog" /noexecute=optin /fastdetect /bootlog
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP2 Safeboot Network" /noexecute=optin /fastdetect /safeboot:network
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP2 Safeboot Minimal" /noexecute=optin /fastdetect /safeboot:minimal

Now when you reboot, and select "Microsoft Windows XP Home Edition" from the initial GRUB Menu, it should then bring up a new Windows bootloader menu with all the above options.  Just try them all out to see if Windows will boot from any of them.  If you do not get a Windows bootloader menu after the initial GRUB menu, then the problem is with GRUB rather than boot.ini.  Obviously, if you manage to get back into Windows, you will have to edit boot.ini again.

---

### Post by chdragonfly on 2007-05-21
even when i use gksuo nautilus, it still says that boot.ini is read only. and now, i have to manually mount the sda1 (windows ntfs ) drive T_T

---

### Post by ugm6hr on 2007-05-21
Use "gksudo nautilus" then right-click boot.ini and select "Properties".  In the "Permissions" tab, select "Read & Write" in the Access entry, assuming owner and group are "root".  Then try to edit again (use any text editor).

Other thing is to ensure that ntfs-3g and ntfs-config are installed (from Synaptic Package Manager).

PS: is there a space in "WINDOW S"?

---

