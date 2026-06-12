---
title: "Please Please Help!! Error 21 grub?"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by jamesjdk on 2007-04-29
Hey everyone, I'm new to Ubuntu and Linux and have just installed Ubuntu 7.04 on a partition on an external hard drive. The idea behind this was so I could try out Ubuntu and all it's features but with out risking damage to my main XP system. Now it's installed I can't boot into either Ubuntu or Xp and always get the following message when I try to.

Grub loading stage 1,5
Grub loading. please wait...
Error 21

the screen then freezes and all I can do is restart by either pressing ctrl-alt-del or push the on off switch at which point the exact same thing happens. I've tried booting with the external hard drive unplugged or by changing boot order by holding esc at start up and it doesn't work.

I've googled this problem and have tried following the solutions given but haven't been able to fix it. Could someone please please provide an idiot proof solution to this problem. I've recently backed up so re-installing windows isn't too much of a problem if need be.

Thank you so much

James

---

### Post by bulldog on 2007-04-29
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

This is what the error means.

You installed ubuntu on a USB device,fine,where did you install GRUB?
If you installed GRUB to (hd0) which is default I understand your problem.

Can you choose to boot from an USB device?
If yes,boot the live cd and boot to the desktop.
Open a terminal and type```
sudo fdisk -l
``` it's a lowercase L not a one.
Post the output to the forum with your USB hdd connected and powered.

---

### Post by silkstone on 2007-04-29
Wait for those who are more knowledgeable to advise you, but I suspect that you will have to use your Windows  CD, go to the recovery console and type fixmbr to restore the master boot record.

Then you should be able to boot into Windows without a complete reinstall.

I think the problem comes with trying to install Ubuntu on an external drive which isn't recognised at boot. I'd suggest partitioning the internal drive and installing Ubuntu on that.

---

### Post by jamesjdk on 2007-04-29
It doesn't give me an option to boot to a usb device but i can boot from the cd. I was wondering if because my external HDD is one of the auto start/shutdown ones it wouldn't have spun up sufficiently so it isn't recognized maybe?

I have no-idea where GRUB was installed, The first I even heard there was something called GRUB was when I saw the error message. I guess if I didn't choose where it is that means it's in the default place
.

---

### Post by jamesjdk on 2007-04-29
> **silkstone said:**
> Wait for those who are more knowledgeable to advise you, but I suspect that you will have to use your Windows  CD, go to the recovery console and type fixmbr to restore the master boot record.

Then you should be able to boot into Windows without a complete reinstall.

I think the problem comes with trying to install Ubuntu on an external drive which isn't recognised at boot. I'd suggest partitioning the internal drive and installing Ubuntu on that.

I had tried to do that when I was installing it in the first place but it was having none of it. Couldn't divide the partition. I'll try using the windows cd. Only problem is I'm at Uni at the moment and need to wait for my parents to post the cd's to me. Typical :)

---

### Post by bulldog on 2007-04-29
I'm not very familiar with your kind of external hdd,I have one myself,it's connected to an USB port,and with a power cord to the outlet.
If I set the power off it won't be recognized,which is pretty clear I think.

Well the problem is:
If GRUB is on hd0 your external disk would be hd1,if the external disk isn't reachable you'll get your error21.
Because windows won't boot either,I think there are some faults in menu.lst and maybe the fstab as well.

The next question would be,how did you choose the external hdd when you installed ubuntu.
I really mean actual,what triggers your external hdd?
Is it always on,or only when you boot the computer or what?

Anyway,I would like you to boot the live cd and perform some commands in the terminal.
If you can put the output of these commands to the forum,we can take a look what's wrong.

---

### Post by Billy McCann on 2007-04-29
I got this same error when I install ubuntu to hd1 and GRUB to hd0.  The fix was to put the second hard drive onto the BIOS devices.  Hope that helps a little.

---

### Post by jamesjdk on 2007-04-29
It's just a normal external hdd like the one you described. I just meant that you don't flick a switch to turn it on, it does that its self when you turn the computer on.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4080       30401   211431465    7  HPFS/NTFS
/dev/sdb2               1        4079    32764536   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by jamesjdk on 2007-04-29
> **Billy McCann said:**
> I got this same error when I install ubuntu to hd1 and GRUB to hd0.  The fix was to put the second hard drive onto the BIOS devices.  Hope that helps a little.

How would go about doing that? Sorry for my Ubuntu ignorance :)

---

### Post by Billy McCann on 2007-04-29
When you first turn on your computer, your motherboard will "post" and you'll see a message.  Something like "press f2 to enter setup".  It might be the del key or the esc key.  But you'll need to press a button to enter into your BIOS, so be looking out for that message.  

Once there, you'll probably see a list of devices.  Now, I've never worked with a USB hard drive.  But with their popularity and all, there simply must be some way of adding it to your BIOS.  You'll see a list of your devices, your hard drive, CD/DVD-ROM drives, floppy, etc.  You'll probably have an empty slot in the list underneath your first hard drive.  Try placing your device there (that's how mine was fixed).  Typically there's a drop down menu to select the device.  If not, try looking around for USB devices.  Each motherboard is setup a little differently so I can't really give step by step instructions.  

But, hey, you're smart.  Once you've gotten into your BIOS just look around and use your head.  Your goal is to put that USB device into your BIOS ... someway .... somehow.

---

### Post by bulldog on 2007-04-29
> **jamesjdk said:**
> It's just a normal external hdd like the one you described. I just meant that you don't flick a switch to turn it on, it does that its self when you turn the computer on.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            4080       30401   211431465    7  HPFS/NTFS
/dev/sdb2               1        4079    32764536   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

Hmmm,where's the swap partition?

Perform the next commands in your terminal,one by one,we have to mount your ubuntu to get to the info we need.
```
sudo mkdir /mnt/rescue
sudo mount /dev/sdb2 /mnt/rescue
```

From the next couple of commands can you post the output  to the forum please?
```
cat /mnt/rescue/boot/grub/menu.lst
cat mnt/rescue/etc/fstab
```

---

### Post by bulldog on 2007-04-29
> **Billy McCann said:**
> When you first turn on your computer, your motherboard will "post" and you'll see a message.  Something like "press f2 to enter setup".  It might be the del key or the esc key.  But you'll need to press a button to enter into your BIOS, so be looking out for that message.  

Once there, you'll probably see a list of devices.  Now, I've never worked with a USB hard drive.  But with their popularity and all, there simply must be some way of adding it to your BIOS.  You'll see a list of your devices, your hard drive, CD/DVD-ROM drives, floppy, etc.  You'll probably have an empty slot in the list underneath your first hard drive.  Try placing your device there (that's how mine was fixed).  Typically there's a drop down menu to select the device.  If not, try looking around for USB devices.  Each motherboard is setup a little differently so I can't really give step by step instructions.  

But, hey, you're smart.  Once you've gotten into your BIOS just look around and use your head.  Your goal is to put that USB device into your BIOS ... someway .... somehow.

Can't work :) 
Only if you have  a boot option to boot from an USB device,you can set to do so in the BIOS.
If you don't have such an option,well,you can't.
He can look for an option to set USB as active by boot,this is usual used for mice and keyboards,but maybe it works for an external drive as well.:)

---

### Post by jimrz on 2007-04-29
> **jamesjdk said:**
> I had tried to do that when I was installing it in the first place but it was having none of it. Couldn't divide the partition. I'll try using the windows cd. Only problem is I'm at Uni at the moment and need to wait for my parents to post the cd's to me. Typical :)

it does not need to be your specific win disk. any xp disk (2k,also) will do for the recovery of your mbr. hopefully there is somebody there at uni that has one you can borrow for the short time this operation takes.

---

### Post by Billy McCann on 2007-04-29
> **bulldog said:**
> Can't work :) 
Only if you have  a boot option to boot from an USB device,you can set to do so in the BIOS.
If you don't have such an option,well,you can't.
Right.  The least we can do is tell him where to look though ... just to see *if* his setup allows him to do so.   

> He can look for an option to set USB as active by boot,this is usual used for mice and keyboards,but maybe it works for an external drive as well.:)
That'd be cool.  But I forsee a re-install with / on the first hard drive and /home on the external.  Hope not, but that's what I'd do in those shoes.

---

### Post by bulldog on 2007-04-29
> **Billy McCann said:**
> Right.  The least we can do is tell him where to look though ... just to see *if* his setup allows him to do so.   


That'd be cool.  But I forsee a re-install with / on the first hard drive and /home on the external.  Hope not, but that's what I'd do in those shoes.

Nope,I don't think a reinstall is necessary :) 
I think the menu.lst is pointing to the wrong partition or the wrong hdd.
This kind of things happens a lot when you install on an external disk,which is not listed in the BIOS.
By editing the menu.lst and maybe fstab,we can correct this,and make windows and ubuntu to boot.

EDIT;
But TS has to mount his ubuntu and post the information we need to edit.
If he doesn't do so,well,I can't do anything.

---

### Post by jamesjdk on 2007-04-29
ubuntu@ubuntu:~$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt/rescue
ubuntu@ubuntu:~$ cat /mnt/rescue/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=9b6cd44e-ce6f-4120-af62-8a8a3d62562b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9b6cd44e-ce6f-4120-af62-8a8a3d62562b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=9b6cd44e-ce6f-4120-af62-8a8a3d62562b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu:~$ cat mnt/rescue/etc/fstab
cat: mnt/rescue/etc/fstab: No such file or directory
ubuntu@ubuntu:~$ 

Thanks to everyone helping me on this. It's much appreciated

EDIT: sorry about the smilies they're supposed to be 8 ) (with out the space obviously :)) i couldn't work out how to turn them off. I don't know what's been happening to me lately. I really shouldn't be let near a computer.

---

### Post by bulldog on 2007-04-29
Well the menu.lst looks very good  to me.
To see the fstab ```
cat /mnt/rescue/etc/fstab
```
But I think this should be okay as well :) 

The only thing what concerns me is your not existing swap file.
How much RAM does your computer have?

To give the external hdd time to spin properly you can set the time out to a higher level before it starts to boot.
It's located here,make it 15 to begin with and don't hit enter to boot,just let it do it for it self,we can shorten the time later.```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10   <=== make it 15 and save the file
```

To open the menu.lst to edit ```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
Edit the timeout and save the file.

---

### Post by jamesjdk on 2007-04-29
ubuntu@ubuntu:~$ gksudo gedit /mnt/rescue/boot/grub/menu.lst

(gedit:14498): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


this happened when i put in the code to change the boot time thing. i was able to do it after though.

This is the fstab

ubuntu@ubuntu:~$ cat /mnt/rescue/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=9b6cd44e-ce6f-4120-af62-8a8a3d62562b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=78A80BC4A80B803C /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
ubuntu@ubuntu:~$ 


I have 512 mb of ram. I do remember a message saying that there was no swap partition for some reason now you mention it.

---

### Post by bulldog on 2007-04-29
512 MB of RAM isn't much to go with,and I think you definitely need a swap partition.
The warning with gedit is nothing,don't you worry about that,it's a long existing bug,but it's to small to pay any attention for the developers,it's harmless anyway.

Your fstab is in order too,so it should boot.

The only thing I want to know is the following```
cat /mnt/rescue/boot/grub/device.map
```
Can you post the output to the forum?

---

### Post by medya on 2007-04-29
hey you should recover your MBR boot records using a live CD , read [more here]("http://blog.shevin.info/2007/04/messed-up-boot-loader-dont-worry.html")

---

### Post by bulldog on 2007-04-29
> **medya said:**
> hey you should recover your MBR boot records using a live CD , read [more here]("http://blog.shevin.info/2007/04/messed-up-boot-loader-dont-worry.html")

Yes,thank you for the input :) 
But first we try to make it boot shall we? if we can't get it to work,we'll follow your excellent advice.

Thank you so much.:lolflag:

---

### Post by jamesjdk on 2007-04-29
> **bulldog said:**
> 512 MB of RAM isn't much to go with,and I think you definitely need a swap partition.
The warning with gedit is nothing,don't you worry about that,it's a long existing bug,but it's to small to pay any attention for the developers,it's harmless anyway.

Your fstab is in order too,so it should boot.

The only thing I want to know is the following```
cat /mnt/rescue/boot/grub/device.map
```
Can you post the output to the forum?

ubuntu@ubuntu:~$ cat /mnt/rescue/boot/grub/device.map
cat: /mnt/rescue/boot/grub/device.map: No such file or directory

doesn't look promising.

how would i go about making a swap partition? should i try installing ubuntu again?

---

### Post by bulldog on 2007-04-29
Hmmm,yes reinstalling is quicker,but less fun,and you'll learn nothing at all.

A reinstall is the last thing I would do, try to learn from this experience,you'll get familiar with the command line and the terminal as well,and you learned how to mount your ubuntu and editing some files :) 

We gonna make a device.map,
```
gksudo gedit
```

This will open the text editor with root privileges,type in the empty file 

(hd0)	/dev/sda 
(hd1)	/dev/sdb

Name the file device.map and navigate to the /mnt/rescue/boot/grub folder in your file system and save it there. 

Another question,before you do this,**is the sda hdd inside your computer a Sata hdd or a IDE hdd**??

I ask this because it's just 40GB and when Sata became popular,the hdd's where much larger as far as I know.
If this is an IDE hdd,one with a flat grey cable on a rather large connector on the motherboard,it shouldn't be listed as sda but hda instead.

EDIT:
We can create a swap file later,we only need 1GB free space on a hdd.

---

### Post by jamesjdk on 2007-04-29
> **bulldog said:**
> Hmmm,yes reinstalling is quicker,but less fun,and you'll learn nothing at all.

A reinstall is the last thing I would do, try to learn from this experience,you'll get familiar with the command line and the terminal as well,and you learned how to mount your ubuntu and editing some files :) 

We gonna make a device.map,
```
gksudo gedit
```

This will open the text editor with root privileges,type in the empty file 

(hd0)	/dev/sda 
(hd1)	/dev/sdb

Name the file device.map and navigate to the /mnt/rescue/boot/grub folder in your file system and save it there. 

Another question,before you do this,**is the sda hdd inside your computer a Sata hdd or a IDE hdd**??

I ask this because it's just 40GB and when Sata became popular,the hdd's where much larger as far as I know.
If this is an IDE hdd,one with a flat grey cable on a rather large connector on the motherboard,it shouldn't be listed as sda but hda instead.

EDIT:
We can create a swap file later,we only need 1GB free space on a hdd.

Not quite sure, I have a feeling it's an IDE but not certain. It's a laptop HDD so it wouldn't be as high a capacity anyway. I'll get the screw driver out :)

---

### Post by bulldog on 2007-04-29
Nope don't open the case,please :) 

How old is the laptop?
I'll go for the IDE option :) 
Make the lines in device.map:

(hd0)	/dev/hda
(hd1)	/dev/sdb

And do as told in the previous post :guitar: 

It could explain why windows won't boot,sda doesn't exist,it should be looking for hda!!

We have to modify this in menu.lst and fstab as well,because that could be the windows failure.
You go a head with device.map I look into menu.lst and fstab.:) 

After you saved the device.map in the grub folder perform the command```
ls /mnt/rescue/boot/grub
``` in a terminal and look if the device.map is listed.
```
cat /mnt/rescue/boot/grub/device.map
``` post the outcome to the forum please.

---

### Post by jamesjdk on 2007-04-29
It's deffinitely IDE (don't worry the hdd slides right out :))

i've found the mnt folder but there is nothing inside it. should i create the folders myself?

---

### Post by jamesjdk on 2007-04-29
i also know the external hdd is IDE too if that helps (when i get bored i get a compulsion to dismantle my possessions :)) although it then goes through usb so i don't know if that makes a difference

---

### Post by bulldog on 2007-04-29
You have to edit some things in menu.lst and fstab.
This is how it should look,
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1 <======this one 
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```This is at the end of the menu

```
gksudo gedit /mnt/rescue/boot/grub/menu.lst
```
If done save the file and exit.

Now fstab,
```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb2
UUID=9b6cd44e-ce6f-4120-af62-8a8a3d62562b / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 <=====this one and /media/hda1 on the next line
UUID=78A80BC4A80B803C /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
```
```
gksudo gedit /mnt/rescue/etc/fstab
```
Edit the lines with sda into hda [twice] and save the file and exit.

This should do.

---

### Post by bulldog on 2007-04-29
> **jamesjdk said:**
> It's deffinitely IDE (don't worry the hdd slides right out :))

i've found the mnt folder but there is nothing inside it. should i create the folders myself?
 
It should have a rescue folder and in there your file system.
Oh well,we mount them again :) 
```
sudo mkdir /mnt/rescue
sudo mount /dev/sdb2 /mnt/rescue
```

EDIT;
you can use the terminal to navigate to the grub folder```
cd /mnt/rescue/boot/grub
```
```
gksudo gedit
```
Type the lines in the empty file and save it as device.map.
It should be placed in the grub folder because you're there already.
Try this if the other method isn't working.

---

### Post by jamesjdk on 2007-04-29
ubuntu@ubuntu:~$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt/rescue

ok done that, now do i go back and try the "gksudo gedit" one again?

---

### Post by bulldog on 2007-04-29
see my edit on previous post please.

---

### Post by jamesjdk on 2007-04-29
ok saved the device.map file in the right place

ubuntu@ubuntu:/mnt/rescue/boot/grub$ ls /mnt/rescue/boot/grub
default      e2fs_stage1_5      jfs_stage1_5  minix_stage1_5     stage2
device.map   fat_stage1_5       menu.lst      reiserfs_stage1_5  xfs_stage1_5
device.map~  installed-version  menu.lst~     stage1
ubuntu@ubuntu:/mnt/rescue/boot/grub$ cat /mnt/rescue/boot/grub/device.map
(hd0) /dev/hda
(hd1) /dev/sdb
ubuntu@ubuntu:/mnt/rescue/boot/grub$

---

### Post by jamesjdk on 2007-04-29
have also edited those 2 files

---

### Post by bulldog on 2007-04-29
Now is the time to reboot then :) 
It's possible your ubuntu won't boot,because there's no swap partition.
Try windows first and look for any error you see and write it down,if possible.
You can have a go with ubuntu as well...............but I don't think it will boot without the swap,just give it a try.

---

### Post by jamesjdk on 2007-04-29
No luck i'm afraid i still get the same old error 21 :(

---

### Post by bulldog on 2007-04-29
Hmmm,that's weird :( 
Neither of them will boot with the same error?

Ohoh,forgot something :( 
We had to update grub when we where using the live cd, I'm a fool.


EDIT;
Okay this is what we gonna do.
when you boot and see the grub menu,select windows and hit the 'e' key.
Now you can edit the boot line for windows,it should be listed as sda1 change this in hda1 and if I'm correct you should hit the 'b' key to boot
but read the screen it's explained over there.

I get rusty.

---

### Post by jamesjdk on 2007-04-29
That pesky grub, how do we do that?

---

### Post by jamesjdk on 2007-04-29
What exactly is the grub menu? I've never had an option to select windows.

---

### Post by bulldog on 2007-04-29
Read the edit again :)
What are you talking about?
If you boot from hdd you should see a DOS box with lines which indicates which OS you want to boot.
You should see minimal two entry's for ubuntu and one for windows.
You can select by hitting arrow keys which line you want to boot.

Never seen that?
When do you see the error21?
How do you boot windows?

---

### Post by jamesjdk on 2007-04-29
Sorry, i'm still not sure. when i turn it on i get for about a second the windows logo (at which point i can press esc to change boot order or f10 to enter setup) and then it goes straight to the error. or do you mean the menu i get when i put the linux cd in?

edit: normally i boot windows just by turning the laptop on

---

### Post by bulldog on 2007-04-29
No it shouldn't be that way,you should never see something from windows.
You should see the normal boot post from the BIOS,counting memory and all that,then you should have a black screen with the boot lines listed.
This should be staying there for 15 seconds,because we set it to 15,and the it should boot into ubuntu by default.
In the mean time you can use the arrow keys to choose another boot option like windows,if you hit that one,than you should see the windows boot logo,not before.

Can you boot the live cd once more so we can reinstall GRUB into the MBR of the hdd.
It only cost 5 minutes of typing in a console.

EDIT;
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

After that type```
sudo update-grub
``` and reboot.
If you see the GRUB menu,choose windows and try if it will boot.
You can try ubuntu as well.........well you know.

---

### Post by jamesjdk on 2007-04-29
it says

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

should i try grub-install?

---

### Post by bulldog on 2007-04-29
Nope you should start at the beginning with sudo grub then provide your password.
then the find command and so on.
If you don't get any error you can setup (hd0) in the end and quit.
But as soon you'll get an error it's wrong.

EDIT;
Reading your previous post more carefully,make me think it can't find your ubuntu install.
Your sdb isn't listed in the BIOS,you can't boot from an USB device,so you can't find the ubuntu install.
You only could install ubuntu on the external disk because the live cd recognized it.
But when there's no OS loaded,your external disk isn't enabled in any way.
I'm sorry but I think what you're trying to do isn't possible with this hardware.
The only possible thing to try is to partition your internal hdd in two sections,install windows on the first half and ubuntu on the second half [don't forget a swap partition 1GB]
Use the external hdd as a data disk,because you can only get to this hdd when there's an OS running.
Partition the external with a NTFS partition for windows data and a ext3 partition for ubuntu data,you even could install the ext2FS driver in windows,so you could read and write 
your ubuntu data in windows.
I'm sorry it hasn't worked out as we like it would,but it seems impossible.

---

### Post by jamesjdk on 2007-04-29
it didn't ask me for a password. i put it in anyway but it just said unrecognised command. so i quit and started with the sudo grub again making sure i don't make any mistakes but i still get the "no GRUB directory found" message

---

### Post by jamesjdk on 2007-04-29
> **bulldog said:**
> Nope you should start at the beginning with sudo grub then provide your password.
then the find command and so on.
If you don't get any error you can setup (hd0) in the end and quit.
But as soon you'll get an error it's wrong.

EDIT;
Reading your previous post more carefully,make me think it can't find your ubuntu install.
Your sdb isn't listed in the BIOS,you can't boot from an USB device,so you can't find the ubuntu install.
You only could install ubuntu on the external disk because the live cd recognized it.
But when there's no OS loaded,your external disk isn't enabled in any way.
I'm sorry but I think what you're trying to do isn't possible with this hardware.
The only possible thing to try is to partition your internal hdd in two sections,install windows on the first half and ubuntu on the second half [don't forget a swap partition 1GB]
Use the external hdd as a data disk,because you can only get to this hdd when there's an OS running.
Partition the external with a NTFS partition for windows data and a ext3 partition for ubuntu data,you even could install the ext2FS driver in windows,so you could read and write 
your ubuntu data in windows.
I'm sorry it hasn't worked out as we like it would,but it seems impossible.

Ok well thanks for all your time and help. I think i might leave Ubuntu for now though, this is my only computer so don't really want to risk ruining anything by partitioning. I'm getting a new laptops soon though so i'll have this one to play around with then :) in the mean time i'll just have to wait for the windows cd to turn up in the post.

Thanks again

James

---

### Post by bulldog on 2007-04-29
Yes like I said in my edit,it can't be done,your external hdd isn't recognized at boot time.
It only shows up when there's an OS loaded.

There's one option we didn't try,but you can if you like.
There's something called Super Grub Disk and it can boot almost anything,but I doubt if it will find the external hdd.
You can find it here,
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Maybe it's able to boot windows,otherwise do as I said in my edit and make the internal hdd for windows and ubuntu and the external just for data.

---

### Post by jamesjdk on 2007-04-29
Ok thanks. Might try that tomorrow. Got early lecture tomorrow though so should probably get some sleep. See ya

---

