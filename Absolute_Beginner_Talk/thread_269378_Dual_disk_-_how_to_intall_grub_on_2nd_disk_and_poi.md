---
title: "Dual disk - how to intall grub on 2nd disk and point to 1st disk"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by shyQ on 2006-10-01
I've just added an IDE disk to my Compaq Professional Workstation AP550 and the machine wants to boot from the IDE disk rather than the SCSI disk where I've got my system installed.  I don't want to install Ubuntu on the new disk because it's smaller and slower - I just want to use this device for backup.

I have tried to change the boot order via the BIOS but it doesn't stick, so I'm pretty much stuck with installing GRUB on the IDE disk and pointing to the SCSI disk.  I've gotten the new disk partitioned and I've gotten as far as starting GRUB, but I've pretty much reached the limit of my knowledge.

Help!!

Thanks,
James

---

### Post by shyQ on 2006-10-01
Ok, I've installed grub on the IDE disk (hd0) in the MBR.  The next step appears to be menu.lst - did I screw up by installing on (hd0) instead of (hd0,0)?

J.

---

### Post by bulldog on 2006-10-01
Try ```
sudo upgrade-grub
```

If this hasn't the desired changes,you can do ```
sudo fdisk -l
```
l as in like.

With this info you can alter the menu.lst.

You can alter your menu.lst manually,but just try upgrade grub to see what it brings you.

---

### Post by bulldog on 2006-10-01
> **shyQ said:**
> Ok, I've installed grub on the IDE disk (hd0) in the MBR.  The next step appears to be menu.lst - did I screw up by installing on (hd0) instead of (hd0,0)?

J.

You have one IDE that is (hd0) and your sata (hd1) the option behind the  , means which partition whe're talking about.

Your fstab however calls your sata disk sda,just to know.

Example,the first partition on hd0 is listed as hd0,1

---

### Post by shyQ on 2006-10-01
> **bulldog said:**
> Try ```
sudo upgrade grub
```

sudo: upgrade: command not found

> **bulldog said:**
> If this hasn't the desired changes,you can do ```
sudo fdisk -l
```
l as in like.

returns nothing at all

I'm still confused.  BTW, I'm running off the Live CD - ver 6.06.1.

J.

---

### Post by bulldog on 2006-10-01
This command's should be run from your installed Ubuntu :D

Okay,do the following from the live cd 
```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda /mnt/ubuntu
```

I hope it's sda but we will see ....

EDIT:
Have you any idea on which partition ubuntu's / is installed?
That would help a lot.

---

### Post by shyQ on 2006-10-01
> **bulldog said:**
> ```
sudo mkdir /mnt/ubuntu
sudo mount /dev/sda /mnt/ubuntu
```


[B]ubuntu@ubuntu:~$ sudo mount /dev/sda /mnt/ubuntu
mount: /dev/sda already mounted or /mnt/ubuntu busy
[/B]

And I'm pretty sure the my Ubuntu is on sda.

J.

---

### Post by bulldog on 2006-10-01
If it's already mounted try to click it to see where Ubuntu is installed.

Because you need the partition where it's installed sda1 or sda2 or sda3 

Type ```
 sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

I'm almost certain this fails but try anyway.

---

### Post by jpkotta on 2006-10-01
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

I just wrote the section "Changing the Disk that Grub is installed to", post back if it's unclear or doesn't work.

---

### Post by shyQ on 2006-10-01
> **bulldog said:**
> If it's already mounted try to click it to see where Ubuntu is installed.

Because you need the partition where it's installed sda1 or sda2 or sda3 

Type ```
 sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

I'm almost certain this fails but try anyway.

I can't get into sda1 via Nautilus, but 

sudo gedit /mnt/ubuntu/boot/grub/menu.lst

opened an empty file in gedit.  Wierd.

BTW, my Ubunto is in sda1.

J.

---

### Post by bulldog on 2006-10-01
Very nice HowTo,thanks jpkotta

Okay,do then the mounting again ```
sudo mount /dev/sda1 /mnt/ubuntu 
```
Then
Type ```
 sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by shyQ on 2006-10-01
> **bulldog said:**
> ```
sudo mount /dev/sda1 /mnt/ubuntu 
```

Works much better, and now 

```
sudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

gets me a real menu.lst

---

### Post by bulldog on 2006-10-01
That's what we need to have :D 

Now you have to alter your entry's manually

Can you copy the menu.lst here?

Or try one more time ```
 sudo update-grub
```
I forgot the - the first time,maybe it works fine now.
Close your menu.lst first please.

---

### Post by shyQ on 2006-10-01
> **bulldog said:**
> That's what we need to have :D 

Now you have to alter your entry's manually

Can you copy the menu.lst here?

Here's my menu.lst:

```
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
# kopt=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

My first guess from reading the How-To that jpkotta pointed us to is that I need to change

```
# groot=(hd0,0)
```

to

```
# groot=(hd1,0)
```

but that's just a guess at this point.  Pls let me know if this makes any sense, and if anything else needs to change.

Thanks,
James

---

### Post by bulldog on 2006-10-01
Before altering anything make a copy of your menu.lst,close it first and type
```

sudo cp /mnt/ubuntu/boot/grub/menu.lst /mnt/ubuntu/boot/grub/menu.lst_copy 
```

Then try ```
sudo update-grub
```

If this works we're ready:D 

Otherwise I should only alter (hd0,0) in (hd1,0) for one entry and try to boot into ubuntu with that entry.

If this works you can alter all of them but just to be sure  we test it out.

Noticed you have no entry for your windows.
You can try to copy the following into the end of your menu.lst
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by shyQ on 2006-10-01
Yeah!!!!

I did a foolish, arrogant thing - I changed all of hd0 to hd1 except for the examples, and it worked just fine.  I've got my Ubunto back!!!

Thanks a bunch, bulldog.

Now I just need to get my new drive mounted.  I've added the mount point and edited fstab, I guess I just need to reboot.

I'll be back, hopefully with more success to report.

Thanks,
James

---

### Post by jpkotta on 2006-10-01
You don't need to reboot if the drive is already plugged in.  After putting it in fstab, just ```
sudo mount -a
```

---

