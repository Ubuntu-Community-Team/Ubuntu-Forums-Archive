---
title: "&quot;dual&quot; booting separate hard drives"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-05-28
I have two hard drives installed.

The former one has Dapper Drake (primary slave)

The latter one has Feisty Fawn (primary master)

Grub shows both (hda, hdb or somehthing like that). It allows a selection of which disk to boot from.

Both disks are used on a single person/user computer. Both OSs are set to boot without asking for UserID/Password.

When I select the second drive (Dapper), the OS gets lost or something and I have to do a hard-reset.

How do I make the FF and Grub understand how to boot to the secondary drive?

I am doing this because too, too many times, something has blow up the OS on a hard disk, leaving me no way onto the 'net, but to go to a public terminal.

Thanks.

---

### Post by LaRoza on 2007-05-29
What happens if you select the device before grub loads?

---

### Post by Mark_in_Hollywood on 2007-05-29
I have no idea as to how to do that. The Dell splash screen loads, then a one-line message from Linux:

Starting up . . .

then a menu comes up showing all the hardisks with each operating system interation on it. 

Please advise.

---

### Post by LaRoza on 2007-05-29
When the Dell splash screen comes, look for instructions for entering the bios, usually "esc" or "del" or "f1".

In there, you can select which device to boot from.

This is BEFORE linux or grub loads, so you may have to be quick to see the correct option.

---

### Post by Mark_in_Hollywood on 2007-05-29
OK,

I'm going to have to go offline to reboot (I'm dialup)

I'll be back in 5 minutes.

Please don't leave!!!!!!

---

### Post by LaRoza on 2007-05-29
While I'm waiting, here are some of the methods for various computers for entering bios, just in case the computer doesn't tell you:

Acer® F1, F2, CTRL+ALT+ESC
AST® CTRL+ALT+ESC, CTRL+ALT+DEL
Compaq® 8700 F10
CompUSA® DEL
Cybermax® ESC
Dell® 400 F3
Dell 400 F1
Dell Dimension® F2 or DEL
Dell Inspiron® F2
Dell Latitude Fn+F1 (while booted)
Dell Latitude F2 (on boot)
Dell Optiplex DEL
Dell Optiplex F2
Dell Precision&#153; F2
eMachine&#153; DEL
Gateway® 2000 1440 F1
Gateway 2000 Solo&#153; F2
HP® (Hewlett-Packard) F1, F2
IBM® F1
IBM E-pro Laptop F2
IBM PS/2® CTRL+ALT+INS after CTRL+ALT+DEL
IBM Thinkpad® (newer) Windows: Programs-Thinkpad CFG.
Intel® Tangent DEL
Micron&#153; F1, F2, or DEL
Packard Bell® F1, F2, DEL
Sony® VIAO F2
Sony VIAO F3
Tiger DEL
Toshiba® 335 CDS ESC
Toshiba Protege ESC
Toshiba Satellite 205 CDS F1
Toshiba Tecra F1 or ESC

---

### Post by F_r_e_d on 2007-05-29
I also have 2 separate hard drives.  One has only Windows, and the other has only Linux Ubuntu.

When prompted at startup, I go into my BIOS and make the choice of which operating system to boot to.  (My BIOS shows both hard drives).  When I save and exit my BIOS, the correct OS always loads.

Try to see if you can make the same choice in your BIOS.  Bear in mind that you may have to do a bit of navigating in your BIOS to find where to make the choice, but you should be able to locate the location in your BIOS wothout too much difficulty.

---

### Post by LaRoza on 2007-05-29
> **F_r_e_d said:**
> I also have 2 separate hard drives.  One has only Windows, and the other has only Linux Ubuntu.

When prompted at startup, I go into my BIOS and make the choice of which operating system to boot to.  (My BIOS shows both hard drives).  When I save and exit my BIOS, the correct OS always loads.

Try to see if you can make the same choice in your BIOS.  Bear in mind that you may have to do a bit of navigating in your BIOS to find where to make the choice, but you should be able to locate the location in your BIOS wothout too much difficulty.


I have the same setup, but the OP was unfamiliar with the bios, and I have a suspicion that Dapper has a problem.

---

### Post by Mark_in_Hollywood on 2007-05-29
got into the BIOS -- no prob

BIOS has only 1 way to boot from the hdd, i.e., choices are fdd, cdrom, hdd

however, one can tell the BIOS that hdd1 is primary slave.

This I did and rebooted. 

Dapper's boot started and loaded x, but the mouse locked.

On Ctrl-Alt-Del, the OS shutdown, restarted and I then said restart, reset BIOS to "normal" and here I am.

Next?

---

### Post by LaRoza on 2007-05-29
If you are having a problem with booting Dapper, it is possible that there is a problem with Dapper or the drive. Would reinstalling Dapper be an option?

I cannot stay here, I have my night class soon.

---

### Post by Mark_in_Hollywood on 2007-05-29
Thanks, La Roza,

No the drive was perfect, the OS (Dapper) fully updated. It worked fine for months on end.

Thanks for your time.

Go to class!!!

---

### Post by confused57 on 2007-05-29
You might want to open a terminal, & post your menu.lst:
```
gedit /boot/grub/menu.lst
```

and

```
sudo fdisk -l
```
the -l is a small "L"

If I'm understanding correctly that you haven't found a solution yet.

---

### Post by Mark_in_Hollywood on 2007-05-30
Grub:

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
# kopt=root=UUID=a407f4ea-e921-4cb1-8ee5-9150afbcf153 ro

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a407f4ea-e921-4cb1-8ee5-9150afbcf153 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=a407f4ea-e921-4cb1-8ee5-9150afbcf153 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-28-386 (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (on /dev/hdb1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, kernel 2.6.15-23-386 (recovery mode) (on /dev/hdb1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single 
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu, memtest86+ (on /dev/hdb1) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

AND

mark@Lexington:~$ sudo fdisk -l
Password:

Disk /dev/sda: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4772    38331058+  83  Linux
/dev/sda2            4773        4865      747022+   5  Extended
/dev/sda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10202050560 bytes
255 heads, 63 sectors/track, 1240 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1185     9518481   83  Linux
/dev/sdb2            1186        1240      441787+   5  Extended
/dev/sdb5            1186        1240      441756   82  Linux swap / Solaris

Disk /dev/sdc: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984      251888    e  W95 FAT16 (LBA)
mark@Lexington:~$

---

### Post by confused57 on 2007-05-30
I believe the problem is that your root in the kernel line is /dev/hda1, but "fdisk -l" shows /dev/sdb1...what you can try is highlight your Dapper entry in the grub boot menu, press "e", change the line in your kernel from "root=/dev/hda1" to "root=/dev/sdb1", then press "b" to boot...this is temporary(this will tell you if it works), but you can boot into Feisty & make it permanent.

```
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sdb1 ro quiet splash
```

---

### Post by Mark_in_Hollywood on 2007-05-30
> **confused57 said:**
> I believe the problem is that your root in the kernel line is /dev/hda1, but "fdisk -l" shows /dev/sdb1...what you can try is highlight your Dapper entry in the grub boot menu, press "e", change the line in your kernel from "root=/dev/hda1" to "root=/dev/sdb1", then press "b" to boot...this is temporary(this will tell you if it works), but you can boot into Feisty & make it permanent.

```
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/sdb1 ro quiet splash
```

What does this do? Please let me 

I have two working OSs. 

Feisty on (the ribbon cable) is Primary Master.
Dapper on (ribbon cable) is Primary Slave.

When the computer is powered-up, I get a menu offering to default to the Feisty (generic Linux something).

A "long" list of other OSs appears as options. As you see: /dev/hda or hd1 and now after Feisty /dev/sdb1...2

I want to be able to call/invoke the primary slave in case I blow something up on the Feisty/Pri.Master.

What does your instruction do? I'm not able to follow what your post is about.

---

### Post by confused57 on 2007-05-30
In your grub boot menu, scroll down until you get to  this entry:
```
title Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb1)
```

It will be highlighted, press the "e" key, this will bring up the menu.lst entries that you can edit, press the arrow down to highlight the line beginning with kernel(the one I listed in my previous post, change to root=/dev/sdb1, instead of root=/dev/hda1, then press "b" to boot...you "might" have to press "e" again after you highlight the kernel line.  Note:  You might have to change kernel  root to /dev/hdb1, instead of sdb1, since that's how Dapper recognizes it.

If you ever have to reconnect your Dapper drive as master, you would do the same thing to change root back to (hd0,0) and the kernel root to root=/dev/hda1, then press "b" to boot...if it works, make it permanent in your menu.lst.
Added:  Here's someone who moved their Ubuntu drive from slave to master(using what I just mentioned):
[http://ubuntuforums.org/showthread.php?t=454760](http://ubuntuforums.org/showthread.php?t=454760)

I have a Dell Dimension 4550, and can only boot to the master drive...

---

### Post by confused57 on 2007-05-30
The "e" (edit) method is a little confusing, until you see what each step does.

It might just be easier to boot into Feisty and edit your Dapper entry in your menu.lst:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```

Scroll down to the entry I listed in my last reply, change the kernel root line:
```
title Ubuntu, kernel 2.6.15-28-386 (on /dev/sdb1)
root (hd1,0)
kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/**sdb1** ro quiet splash
initrd /boot/initrd.img-2.6.15-28-386
savedefault
boot
```
quit & save

If /dev/sdb1 doesn't boot Dapper, then try /dev/hdb1

Added:  The "e" editing of your grub boot menu is a temporary way of booting into a Linux OS...it's especially helpful if you can't boot into any of your OS.  Once you find that editing this way boots into your Ubuntu, then you make it permanent in your /boot/grub/menu.lst.

---

### Post by Mark_in_Hollywood on 2007-05-30
OK, two posts in a row,

I followed the procedure in your post, #16 in this thread.

in GRUB /dev/hda1 changed to /dev/sdb1 and 'b' 

shutdown and restart -- very long time

up came:

/dev/sdb1 does not exist -- then BusyBox v. 1.01

#

I did: sudo shutdown -r now , but nothing happened, I did ctrl-alt-del and am back in Feisty OK

---

### Post by confused57 on 2007-05-30
> **Mark_in_Hollywood said:**
> OK, two posts in a row,

I followed the procedure in your post, #16 in this thread.

in GRUB /dev/hda1 changed to /dev/sdb1 and 'b' 

shutdown and restart -- very long time

up came:

/dev/sdb1 does not exist -- then BusyBox v. 1.01

#

I did: sudo shutdown -r now , but nothing happened, I did ctrl-alt-del and am back in Feisty OK

Looks like it's going to have to be /dev/hdb1, which is how Dapper recognizes the drive  the root partition is on...also, you might want to enter your bios setup and make sure the slave drive is set to "auto", on my Dell it's off by default.

---

### Post by confused57 on 2007-05-30
Did changing your kernel root to  /dev/hdb1 happen to boot your Dapper drive?

---

### Post by Mark_in_Hollywood on 2007-05-31
> **confused57 said:**
> Did changing your kernel root to  /dev/hdb1 happen to boot your Dapper drive?

If by "changing your kernel root  . . " you mean following the instructions you gave about temporarily modifying the grub menu line 

kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash 

from /dev/hda1 to /dev/sdb1

I thought that is what I did and then posted that the mouse locked and, yes it did look like it booted Dapper.

Signed: Confused 58, 59, 60 . . .

---

### Post by confused57 on 2007-05-31
> **Mark_in_Hollywood said:**
> If by "changing your kernel root  . . " you mean following the instructions you gave about temporarily modifying the grub menu line 

kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash 

from /dev/hda1 to /dev/sdb1

I thought that is what I did and then posted that the mouse locked and, yes it did look like it booted Dapper.

Signed: Confused 58, 59, 60 . . .

I was referring to trying /dev/hdb1:

kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash

from /dev/hda1 to /dev/hdb1

instead of /dev/sdb1

---

