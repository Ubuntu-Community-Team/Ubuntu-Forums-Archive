---
title: "windows XP / ubuntu"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by JaK0121 on 2007-07-18
i know youve probably heard this problem 100 times before.. 

i was using windows XP until yesterday when i installed ubuntu. 
the installation went fine. but i wasnt given the option of partitioning ubuntu / windows 
after all the updates had downloaded, i restarted my computer. 
i expected to be given the option of either running windows XP or ubuntu. 
my computer just loaded up ubuntu straight away. 
surely ubuntu couldnt have cleared off windows XP in the 5-10 minutes that it took to install.. 



have i lost windows XP? 

is there anyway for me to use XP on my computer still? 
-if so how do i go about this? 

- have i lost all of my files that i had on my windows XP


i would greatly appreciate any help and support .....

---

### Post by misfitpierce on 2007-07-18
If it was not on the boot grub screen then most likely yes... prob for the best tho :) lol

---

### Post by Gone fishing on 2007-07-18
Seems odd as the installer does give you a range of partitioning options including resizing the Windows partition. Anyway I&#8217;d restart the PC on the Ubuntu installation disk and open gparted from the menu if the NTFS partition is still there you probably still have Windows and this can be fixed using the XP CD if not it&#8217;s gone.

---

### Post by stinger30au on 2007-07-18
are you sure you installed it and are not still booting for the cd?

---

### Post by JaK0121 on 2007-07-18
im definatly still not running it from the disc still...    
i shall try the other options you have posted and if it still doesnt work ill reply back here to update you with what ive found... 

thanks for such a quick response,          talk soon

---

### Post by tcoffeep on 2007-07-18
When I was still using windows, I had to push ESC to get to the GRUB menu, and I could pick Windows from there :)

---

### Post by Carlos Santiago on 2007-07-18
You probably select «use entire disk» when you were installing.

This option, as it say, will use ALL your disk.

If you did select that option, the data you have on your disk was clear.

Next time pay attention to the messages and options presented to you.

---

### Post by nero04 on 2007-07-18
Hey, I have a pretty similar problem to the one discussed here. I completely formatted my PC a couple of days ago. First I installed Windows XP and afterwards Ubuntu on another partition. Before I installed Ubuntu, I was able to boot XP without any problems occuring. Afterwards, GRUB didn't seem to know anything about Windows anymore and always booted Ubuntu straight away. There is no entry about XP in the Grub menu either. Still I know the windows partition was not formated by ubuntu since it is linked onto my Ubuntu desctop (hda5) and I can see that all the Windows-files are still there. I repeted the whole installation of XP and Ubuntu abput three times but it doesn't change a thing.
Does anybody know how to fix this problem and get XP back into the Grub menu?

---

### Post by kirios on 2007-07-18
> Still I know the windows partition was not formated by ubuntu since it is linked onto my Ubuntu desctop (hda5) and I can see that all the Windows-files are still there
[COLOR="Navy"][COLOR="Sienna"]Are you sure your Windows install was on /dev/hda5? XP usually insists on being installed to a primary partition. 
It would help if you could post the contents of /etc/fstab and /boot/grub/menu.lst.[/COLOR][/COLOR]

---

### Post by nero04 on 2007-07-18
Well, during the Windows installation I first partitioned my harddisk. back then the partition was called E:
when I installed Ubuntu it was called hda5 for some reason and during the installation I selected to configure hda5 as something called /media or so just as I selected the partition hda1 as swap for example.

Here is the contend of my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and here is /boot/grub/menu.lst

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
timeout		3

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
# kopt=root=/dev/hda6 ro

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

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by kirios on 2007-07-18
[COLOR="Sienna"]Hmm... You could try making an entry for XP in /boot/grub/menu.lst [/COLOR]
# title Windows XP
# root (hd0,4)
# makeactive
# chainloader +1
[COLOR="Sienna"]But I don't think XP will boot from a logical partition. I would suggest booting from the Live CD again, deleting all existing partitions and setting up /dev/hda1 as a Windows partition, /dev/hda5 as swap, and /dev/hda6 as /. Then install XP to the first partition and Ubuntu to /dev/hda6.[/COLOR]

---

### Post by jvc26 on 2007-07-18
> **JaK0121 said:**
> i know youve probably heard this problem 100 times before.. 

i was using windows XP until yesterday when i installed ubuntu. 
the installation went fine. but i wasnt given the option of partitioning ubuntu / windows 
after all the updates had downloaded, i restarted my computer. 
i expected to be given the option of either running windows XP or ubuntu. 
my computer just loaded up ubuntu straight away. 
surely ubuntu couldnt have cleared off windows XP in the 5-10 minutes that it took to install.. 



have i lost windows XP? 

is there anyway for me to use XP on my computer still? 
-if so how do i go about this? 

- have i lost all of my files that i had on my windows XP


i would greatly appreciate any help and support .....

Back to the OP, I'm not sure whether you've actually had anything useful thus far. Basically, there is a chance if you selected 'install over entire hard disk' rather than manual install and resizing your partitions you could have overwritten the disk. If you didnt select this, then it is more likely that your partition is there.

First:
```

sudo fdisk -l

```
note l is a lower case L, not an i or j or other letter like that.
That will list your partitions, if Windows is still there it will show up like as not as an NTFS partition.

Once its there its a fairly simple matter of checking GRUB recognises where the partition is, (cat /boot/grub/menu.lst) and posting that output up here, then we can help you some more.
Il

---

