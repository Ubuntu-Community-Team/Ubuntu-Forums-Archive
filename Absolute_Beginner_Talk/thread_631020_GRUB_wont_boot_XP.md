---
title: "GRUB wont boot XP"
date: 2007-12-04
forum: Absolute Beginner Talk
---

### Post by Mr.Wellington on 2007-12-04
Hello everyone. This is my first foray into Linux whatsoever. 

With the help of a friend over Pidgin, I was able to uninstall Vista and Install XP.  I then dual-booted Gutsy onto my HP dv6409 Laptop and, among other problems (wireless and graphics not loading), GRUB will not load Windows XP. 
My contact had to leave and now I want to get this finished before going to bed tonight. I am on another machine because I only have wireless in my room.
I....forgot how to get to the grub text file so i can't remember what he told me to type.

*EDIT*I did a quick google and found the command. 

> 
title Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


this is what he told me to copy+paste into the bottom of the document. When i try and boot the XP partition, it gives me 

> 
Error 12: Invalid Device Requested


Hope this additional information helps.

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-04
xp will only boot from a primary partition when useing the grub or sumthing like that Dont really know how it works but prity shur.
ummm i would wait for someone else to give you some advice before acting

---

### Post by Mr.Wellington on 2007-12-04
i added some information on the first post.

---

### Post by mikewhatever on 2007-12-04
Can you post the output of <sudo fdisk -l> from the Terminal in Ubuntu.

---

### Post by Amstell on 2007-12-04
can you post your /boot/grub/menu.lst......

that will give us an idea...

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-04
could be the problem were windows xp is not on a primary partion 
to be safe i would in stall vista and xp on 2 diff primary partions and then make a 3rd for all your linux stuff and then put all of your linux file system in there 

how ever to do this you have to kill the xp you have allready

could be the problem were hd0,0 is not the right partion
in this case you just have to find out what part it is and  change the second 0 to what ever the part is

partioning is hard the first few times you do it but its really easy after you get it 
a google search is always help full 
this is a link to a older thead that is very similar (and posibly the same) problem your haveing
["]http://ubuntuforums.org/archive/index.php/t-72338.html]("http://ubuntuforums.org/archive/index.php/t-72338.html[/URL)

---

### Post by Joeb454 on 2007-12-04
The grub error looks like the menu.lst file is pointing grub to the wrong partition on the drive, I've had that error before, can you post what **mikewhatever** suggested?

---

### Post by Mr.Wellington on 2007-12-04
This post is a bump post so that I can find it when i get to school: I commune to college everyday. I'll plug in and we'll figure this out. 

This single post will be edited/post will be bumped when I get what Mikewhatever and Amstell asked for.

<<joe>>: you've linked me to list of the entire forum. There is no post there.

Thank you guys.

---

### Post by Mr.Wellington on 2007-12-04
Sudo fdisk -l reads:
> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc202b441

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        9813    78814890    f  W95 Ext'd (LBA)
/dev/sda2   *       13731       14593     6932047+   7  HPFS/NTFS
/dev/sda3            9814        9965     1220940   82  Linux swap / Solaris
/dev/sda4            9966       13730    30242362+  83  Linux
/dev/sda5               2        9813    78814858+   7  HPFS/NTFS

Partition table entries are not in disk order


/boot/grub/menu.lst reads:
> # menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=8d80f1fe-8cfc-4471-986d-e585f7b1ed77 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash acpi=off

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8d80f1fe-8cfc-4471-986d-e585f7b1ed77 ro quiet splash acpi=off
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=8d80f1fe-8cfc-4471-986d-e585f7b1ed77 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

title		Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

hope this helps

all hp laptops include a "recovery" partition. Thats the small one. I have 4 partitions. One for xp. One for the swap. one for ubuntu. one for the recovery.

---

### Post by Mr.Wellington on 2007-12-04
Sorry to double post. This is a bump

---

### Post by Mr.Wellington on 2007-12-04
bumpu again. i apologize.

---

### Post by rmalouin on 2007-12-04
I have found two products work well for seeing what's up with the MBR.

[http://www.terabyteunlimited.com/](http://www.terabyteunlimited.com/)

Bootit, you can use this free for 30 days, it will tell you all you want to know about your partitions and where windows is.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

super grub will allow you to make all kinds of changes to grub.

Good Luck

---

### Post by psusi on 2007-12-04
What happens when you try the Vista boot option, because that looks like it should work.

---

### Post by meierfra on 2007-12-04
You have two different NTFS partitions (sda2 and sda5).  sda2 is about 7GB and sda5 about 79GB. One of them is your Windows XP. What is the other? (You said that you uninstalled Vista) And which one is Windows XP?

---

### Post by dfreer on 2007-12-04
The OP has a recovery partition (containing the preinstalled Vista), and the windows XP partition. We're assuming that sda5 is the Windows XP partition.

So that means that to boot windows XP, the root should be set as (hd0,4) correct? Is this affected by what appears to be an extended/logical partition (/dev/sda1)?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-12-10
hey sorry about that bad link and for takeing for ever to get back to you
but if you xp is on the sda5 partion that is in side of an extended partion 
and from problems i have had that dosent work well i dont rember why and the only fix i know is to reinstall windows on a non secondary partion 
now just kuss i dont know a better solution to you problem dosent mean it exist so 
i will do some more digging see if we cant fix this with out reinstalling every thing or changeing partions

---

### Post by Jer Engineer on 2008-02-19
Yo, Sorry for resurrecting an old thread but I have a similar laptop so I thought I would throw  my question in here. In a nutshell, I have a HP DV9438ca, came with vista, I installed ubuntu on the second HD. Then after vista made me mad for the last time I installed XP over it on the first HD. This gave me a nice fresh XP that worked but killed my grub. So I used the ubuntu cd to "rescue" and fixed grub. Now I boot into ubuntu just fine but for the life of me cant get back into XP, I have searched far and wide for answers and have been to the grub site [http://www.gnu.org/software/grub/manual/grub.html]("http://www.gnu.org/software/grub/manual/grub.html")


Here is my menu.lst

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a00f0df-9fa0-4900-8966-c7cab93acb7d ro noapic irqpoll noirqdebug quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=3a00f0df-9fa0-4900-8966-c7cab93acb7d ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Other operating systems:
root


This entry automatically added by the Debian installer for a non-linux OS
on /dev/sda1
title		Windows XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

#This is one thing I tried
#title		Windows XP (loader)
#unhide 		(hd0,1)
#hide 		(hd0,0)
#rootnoverify 	(hd0,1)
#chainloader 	+1
#makeactive
#boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1





and my sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdffa3cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       18401   147798000   1f  Unknown
/dev/sda2   *       18402       19315     7338512    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc55952a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       13995   112414806   83  Linux
/dev/sdb2           13996       14593     4803435    5  Extended
/dev/sdb5           13996       14593     4803403+  82  Linux swap / Solaris


Any Ideas besides reinstalling Ubuntu, I worked too hard to get it just how I like it :)

---

