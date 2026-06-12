---
title: "[SOLVED] Possible grub error...."
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by BoJaNgLes19 on 2008-03-31
Ok so here is my problem:  I successfully installed Ubuntu Gutsy Gibbon on my second hdd, with the first having Vista on it.  It was easy and straightforward until I got the part where I had to reboot.  I took the CD out as it said, but on reboot Vista took over (im assuming from GRUB preferences).  Everytime I tried to reboot, Vista took over, and I had no GRUB screen option to choose my OS.  I went through the install again, completely wiping the hdd and starting over.  Same problem.  So then i decided to boot using the cd, and it worked.  On the main CD screen, I just chose the option "Boot from first Hard Drive."  And on doing so, I was redirected to a GRUB screen, where I could choose which OS I wanted to boot.  

So then I went into the terminal on my Ubuntu OS, and ran the command:

sudo gedit /boot/grub/menu.lst

I got my grub options pulled up, but I dont know how or if I should edit them.  Any ideas as to why that option on my install cd directs me to that GRUB page but every time I just do a plain reboot Vista takes over and I dont even get a choice?

Here is my menu/lst (boot/grub) gedit:



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
# kopt=root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
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
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


If anyone could help me with this problem that would be great!  :)  I dont know if this is already a bug or not, so sorry if I am wasting your time

---

### Post by Duck2006 on 2008-03-31
From the  Applications>>Accessories>>Terminal type

sudo fdisk -l

and post the output hear.

---

### Post by Inxsible on 2008-03-31
```
 map        (hd0) (hd1)
map        (hd1) (hd0)
``` these two lines are strange here (at the very end in the Windows section). Its mapping the 1st drive to the 2nd and 2nd to the first. Maybe that's why you dont get the grub.
Just remove those 2 lines and try again. in case it doesn't work still, you can always add those two lines back in.

---

### Post by bumanie on 2008-03-31
If vista is on your first hdd and ubuntu on your second hdd the /boot/grub/menu.lst indicates that grub has reversed the drives . Vista should be (hd0,0) and ubuntu should be (h1,0)
In this section change the (hd0,0) entries to (hd1,0)
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet

title Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=9411f1b1-2c10-4663-b49d-1605f9c08a31 ro single
initrd /boot/initrd.img-2.6.22-14-generic

title Ubuntu 7.10, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
And in this section change the (hd1,0) to (hd0,0)
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

Before you begin editing do a backup of /boot/grub/menu.lst with the following command in terminal
> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
This way if something goes wrong, you have your original list still in tact.

---

### Post by BoJaNgLes19 on 2008-03-31
here you go:

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by Duck2006 on 2008-03-31
No

sudo fdisk -l 

(L as in small l)

Thats what i am thinking "bumanie" (may be wrong)

---

### Post by BoJaNgLes19 on 2008-03-31
Im going to try these, but I might not get to it until later tonight.  Which should I try first?

Should I edit it so Vista becomes (hd0,0) and ubuntu becomes (h1,0) 

or

Take the last two map lines out.


Thanks I just want to get this right as I really would rather avoid having to rebuilding Vista.  Or will these even affect it?

Sorry Im new to this but im trying to learn quickly

---

### Post by Inxsible on 2008-03-31
> **BoJaNgLes19 said:**
> Im going to try these, but I might not get to it until later tonight.  Which should I try first?

Should I edit it so Vista becomes (hd0,0) and ubuntu becomes (h1,0) 

or

Take the last two map lines out.


Thanks I just want to get this right as I really would rather avoid having to rebuilding Vista.  Or will these even affect it?

Sorry Im new to this but im trying to learn quickly If you know for sure that your Vista is in the first drive and Ubuntu in the second, then try bumanie's solution. 

Although that mapping is strange, why would you map hd0 to hd1 and then hd1 to hd0 again ?

---

### Post by BoJaNgLes19 on 2008-03-31
O ok here sorry about that:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd355d355

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312568832    7  HPFS/NTFS

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20542053

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       24416   196121488+  83  Linux
/dev/hdb2           24417       24792     3020220    5  Extended
/dev/hdb5           24417       24792     3020188+  82  Linux swap / Solaris



Yea I just want to do this the right way without screwing my system over.  Thanks for your help.  The community here is amazing.  Hope this helps you (and me lol)

---

### Post by Duck2006 on 2008-03-31
When you do the sudo fdisk -l it will show you as to whet is on what drive and what partition the OP in in. So do that first and then edit your menu.lst to the right partition for the wright OP's.

---

### Post by BoJaNgLes19 on 2008-03-31
Ok so i think i get thank you! 

But could you possibly show me where in my menu.lst i would do this?  I believe i am basically doing what bumanie said?  Sorry for the hassle

---

### Post by bumanie on 2008-03-31
Look down near the end of the list. That's why I left the headings there as they are a good pointer to the part of the list you need to alter. Please ensure you make a back up copy. What I've said should work, but sometimes there are idiosyncratic conflicts with a particular machine that makes grub not work as it should that's why a backup list is important. The drive map is a bit strange to have been added by grub itself, but it shouldn't make too much difference because it is telling grub to check both hdd in the opposite order. It is actually a trick used sometimes to trick grub into thinking windows is on a primary drive if it has been installed on a secondary drive (but that's not the case with your installation).

---

### Post by BoJaNgLes19 on 2008-04-01
hmm... problem still

ok so I tried your suggestion by renaming: Vista becomes (hd0,0) and ubuntu becomes (h1,0) 

Same problem, Vista took over.  So i inserted the CD, and again went to the last option "Boot from first hard drive."  It redirected me to the grub boot page, but all of the options would not boot, including vista.  So i shut her down and booted normally, (hence how I am online) and I am in vista now.  I cant even get into my Ubuntu, except for the cd version.

Anyone have help?

---

### Post by Duck2006 on 2008-04-01
You can use EasyBCD boot manager to boot into ubuntu.

[www.freewarefiles.com/EasyBCD_program_21892.html](www.freewarefiles.com/EasyBCD_program_21892.html)

---

### Post by BoJaNgLes19 on 2008-04-01
Thank you!  

Except I dont know how to change what I need to change.  The program looks easy enough to use, but when I navigate through it I dont know where to start

---

### Post by Duck2006 on 2008-04-01
This is the Documentation for EasyBCD. I should help you out.

[http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=42E0F08F84C3B4A2068E29686840CB31](http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home;jsessionid=42E0F08F84C3B4A2068E29686840CB31)

---

### Post by Duck2006 on 2008-04-01
This Documentation is for setting it up for ubuntu.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by BoJaNgLes19 on 2008-04-01
Aha! one last thing:

I am adding the linux bootloader to the windows vista one , but do i check the box that says 

"Grub isnt installed in the bootsector" 

??  Or do i leave it alone because there is one there already...?

---

### Post by Duck2006 on 2008-04-01
> **BoJaNgLes19 said:**
> Aha! one last thing:

I am adding the linux bootloader to the windows vista one , but do i check the box that says 

"Grub isnt installed in the bootsector" 

??  Or do i leave it alone because there is one there already...?

The bootsector is the MBR, what bootloader do you have in there?

---

### Post by BoJaNgLes19 on 2008-04-01
Sry man I dont know what you mean here.

I went to the add/remove entries section, and was going to add my linux one (it recognizes it but didnt have an "entry" for it)

Before that i went to the "manage bootloader" button and clicked "write MBR" and it gave me a prompt saying it would make the changes at the restart. 

I didnt know it would do that :(  

Am i totally off in what i am doing here?

---

### Post by Duck2006 on 2008-04-01
When you boot the system do you get a grub menu or does it just boot in to windoze?

---

### Post by BoJaNgLes19 on 2008-04-01
straight into windows

---

### Post by BoJaNgLes19 on 2008-04-05
well, after all that work it seems all i had to do was go into my bios and change the hdd boot order.  Everything works great now.  thanks to all who helped!

---

