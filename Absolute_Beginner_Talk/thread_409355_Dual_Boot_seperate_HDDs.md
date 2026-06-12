---
title: "Dual Boot: seperate HDDs"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by mikey5555 on 2007-04-14
Hello All.... 
I'm a noob to UBUNTU, so be gentle...:) :) 
I need some clarification about Dual Boot.  My scenario:  P4D 3GHz, 1GB RAM, 2ea 160GB SATA HDDs, IDE CD-R/RW, Diamond (ATI/RADEON) X300SEHM PCIE 256MB.  I currently have UBUNTU 6.10 Edgy on one HDD, and WinXP Pro on the other.   
Currently I have been shutting down PC and physically connecting whichever drive I wish to boot from (while leaving the other drive disconnected), then boot system to OS installed on that drive.      
I would like to configure this system to present me with the ability to choose the OS (or drive) to boot from, without doing all that "connect=disconnect" jaz every time I want to boot to the other OS.  
Reading here, it seems that grub is what I need (?).  Given my scenario, is it possible to make this config change without having to re-install either OS?  I am not afraid of CLI, but not very knowledgable about this OS, yet.
Any guidance. pointers, or assistance will be most appreciated.

Regards....

Mikey5555

---

### Post by sewercake on 2007-04-14
How did you download ubuntu? If it was from liveCD, Then GRUB is automatically isntalled. But yes, to answer your question, GRUB is what you need. Have you tried hooking up both at the same time? does it automatically boot from the master drive? If so, go download grub.
hope this helps



-Sewercake

---

### Post by confused57 on 2007-04-14
> **mikey5555 said:**
> Hello All.... 
I'm a noob to UBUNTU, so be gentle...:) :) 
I need some clarification about Dual Boot.  My scenario:  P4D 3GHz, 1GB RAM, 2ea 160GB SATA HDDs, IDE CD-R/RW, Diamond (ATI/RADEON) X300SEHM PCIE 256MB.  I currently have UBUNTU 6.10 Edgy on one HDD, and WinXP Pro on the other.   
Currently I have been shutting down PC and physically connecting whichever drive I wish to boot from (while leaving the other drive disconnected), then boot system to OS installed on that drive.      
I would like to configure this system to present me with the ability to choose the OS (or drive) to boot from, without doing all that "connect=disconnect" jaz every time I want to boot to the other OS.  
Reading here, it seems that grub is what I need (?).  Given my scenario, is it possible to make this config change without having to re-install either OS?  I am not afraid of CLI, but not very knowledgable about this OS, yet.
Any guidance. pointers, or assistance will be most appreciated.

Regards....

Mikey5555

Connect both of your hard drives, but set your bios to boot  the Ubuntu drive before the Window's drive...then see the 3rd link in my signature for adding an option in grub to boot your Windows drive.

Added:  Make sure to connect your Ubuntu drive to the same SATA controller that you do when you boot your Ubuntu drive connected as the only drive.

---

### Post by regomodo on 2007-04-14
Hi, I tried to do what you did but Grub failed to configure correctly. Would never find the XP partition. I tried to edit menu.lst but it didn't work. Possibly because my device.map was incorrect. I checked the Grub website for help but it's very long so i couldn't be arsed.

Instead i used Acronis OS selector (installed on the XP partition) but i didn't like, very slow.

In the end i put my Ubuntu partition on my xp partition.

Be aware that Grub doesn't like you setting up Ubuntu on a 1st or second HDD using the default "hd0" hard drive. 

For example, i installed Ubuntu and XP on hd2 (a sata drive setup to boot first in BIOS) but left the grub boot placement on hd0. Needless to say it didn't work. I got round that by disconnecting the PATA drives and did the install (which configured Grub correctly with XP & Ubuntu) then setup my fstab later. I now realise that this wasn't necessary. 

I'm sure that was a little waffly and badly worded but i hope that's of some help

---

### Post by mikey5555 on 2007-04-14
confused57, I followed your instructions (3rd link in your sig).  I now get the grub menu (text), but for some reason I cannot make a selection before the countdown finished.  It appears my kbd is "locked" untill the countdown completes.  It works fine before grub (ie..  del takes me to setup, Pause key works, num lock, etc..), and after booting into xP.  Got any suggestions?  FYI:  I have multiple PCs sharing one monitor/kbd via belkin Omniview SE 4 Port switch, and hve never had this particular problem b4 (over 5 years and mannny PCs)

mikey5555

---

### Post by confused57 on 2007-04-14
I have a KVM switch, but I'm not familiar with kbd.  If you have a USB keyboard, maybe this will help:
[http://ubuntuforums.org/showthread.php?t=398443&highlight=usb+keyboard](http://ubuntuforums.org/showthread.php?t=398443&highlight=usb+keyboard)

I don't suppose extending the timeout would help?  You can edit your /boot/grub/menu.lst, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

---

### Post by mikey5555 on 2007-04-15
confused57,
Thanks for the info, but I finally resolved this one by simply changing BIOS to NOT enable NumLock at boot, and I now can access the menu and select the OS (I also extended the timeout to 30 sec for my convience).

Your instructions were very useful.  everything seemed to progress smoothly, including your "Dualboot 2 HD" link.  However, when I rebooted from XP and selected from the GRUB Menu - "Ubuntu, kernel 2.6.17-11 generic" to boot to Ubuntu, I recieved the following error - 


[B]Busy Box v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control is turned off
(initramfs)_[/B]       <-- (this is the prompt at which the system stops)



I am not so familiar with Ubuntu (or UNIX in general) as I'd like, so I need the assistance of the fine folks in this forum again...

Regards...
mikey5555

---

### Post by confused57 on 2007-04-15
> **mikey5555 said:**
> confused57,
Thanks for the info, but I finally resolved this one by simply changing BIOS to NOT enable NumLock at boot, and I now can access the menu and select the OS (I also extended the timeout to 30 sec for my convience).

Your instructions were very useful.  everything seemed to progress smoothly, including your "Dualboot 2 HD" link.  However, when I rebooted from XP and selected from the GRUB Menu - "Ubuntu, kernel 2.6.17-11 generic" to boot to Ubuntu, I recieved the following error - 


[B]Busy Box v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
enter 'help' for a list of built-in commands.

/bin/sh: can't access tty: job control is turned off
(initramfs)_[/B]       <-- (this is the prompt at which the system stops)



I am not so familiar with Ubuntu (or UNIX in general) as I'd like, so I need the assistance of the fine folks in this forum again...

Regards...
mikey5555

Does your Ubuntu drive still boot when it is connected as the only hard drive?  If it does, leave it connected as is, then connect your Window's drive to the other SATA connector...make sure in bios that your controller that your Ubuntu drive is connected to is set to boot before the Window's drive.

---

### Post by mikey5555 on 2007-04-16
I have the Ubuntu drive connected to the SATA1 port, and the XP drive connected to the SATA3 port.  Ubuntu has been connected to SATA1 all along, and XP drive has been on SATA3 and SATA2 (after different reinstalls of Ubuntu) with no change in the final results.  The Ubuntu drive (Maxtor 160GB) is the 2nd boot device in my BIOS (CR ROM is 1st device) and the XP drive (Western Digital 250GB)  is not included in my boot order.  I do NOT have an entry in BIOS for a third boot drive, so the XP drive is not even on the "Boot Order" list in BIOS.
Now, with or without the XP drive connected, Ubuntu still gives the same error and the system does not boot all the way into Ubuntu.  Is this something I could correct from the command line given in the previous message?  If not, I will have to reinstall and start from scratch.  
Any ideas as to why this is happening?  I've tried this config 3 times now (with a complete reinstall of Ubuntu each time), and the results have been the same:  After I complete all instructions for installing and updating Ubuntu and modifying the file menu.lst,  I reboot to Ubuntu, (I did not attempt to go to XP untill after completing all Ubuntu install/config/update chores and rebooting to Ubuntu at least twice), then reboot and select XP and system boots to XP.  When I reboot from XP to return to Ubuntu, the problem pops up and I cannot boot Ubuntu completely.

Regards...
mikey5555

---

### Post by Razorback on 2007-04-16
[http://ubuntuforums.org/showthread.php?t=337621&highlight=Busy+Box+v1.1.3+%28Debian+1%3A1.1.3-2ubuntu3%29+Built-in+shell+%28ash%29](http://ubuntuforums.org/showthread.php?t=337621&highlight=Busy+Box+v1.1.3+%28Debian+1%3A1.1.3-2ubuntu3%29+Built-in+shell+%28ash%29)

---

### Post by confused57 on 2007-04-16
> **mikey5555 said:**
> I have the Ubuntu drive connected to the SATA1 port, and the XP drive connected to the SATA3 port.  Ubuntu has been connected to SATA1 all along, and XP drive has been on SATA3 and SATA2 (after different reinstalls of Ubuntu) with no change in the final results.  The Ubuntu drive (Maxtor 160GB) is the 2nd boot device in my BIOS (CR ROM is 1st device) and the XP drive (Western Digital 250GB)  is not included in my boot order.  I do NOT have an entry in BIOS for a third boot drive, so the XP drive is not even on the "Boot Order" list in BIOS.
Now, with or without the XP drive connected, Ubuntu still gives the same error and the system does not boot all the way into Ubuntu.  Is this something I could correct from the command line given in the previous message?  If not, I will have to reinstall and start from scratch.  
Any ideas as to why this is happening?  I've tried this config 3 times now (with a complete reinstall of Ubuntu each time), and the results have been the same:  After I complete all instructions for installing and updating Ubuntu and modifying the file menu.lst,  I reboot to Ubuntu, (I did not attempt to go to XP untill after completing all Ubuntu install/config/update chores and rebooting to Ubuntu at least twice), then reboot and select XP and system boots to XP.  When I reboot from XP to return to Ubuntu, the problem pops up and I cannot boot Ubuntu completely.

Regards...
mikey5555

Try booting up the live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small  "L"

If you can determine which is your root partition from the above command, try booting up your system(without the live cd), highlight your Ubuntu entry, press "e", then in the kernel line, make sure the root=/dev/sda1, or whatever fdisk shows is correct, change if it isn't, then press "b" to boot.  If it works, it can be made permanent in your /boot/grub/menu.lst.

---

### Post by confused57 on 2007-04-16
Here's a thread that you might want to read the last few posts, someone with a similar problem:
[http://ubuntuforums.org/showthread.php?t=179902&page=6](http://ubuntuforums.org/showthread.php?t=179902&page=6)

He was able to get his system to boot by switching which SATA controller his Windows & Ubuntu drives were connected to.

---

### Post by mikey5555 on 2007-04-17
confused57,
	I reinstalled Ubuntu, and edited menu.lst per your instructions.  Now on reboot, when I select Windows XP, I get an error about an invalid device string, and then it returns to the Grub menu for selecting an OS to boot.  I am attatching the results of the "sudo fdisk -l" command along with my fstab and menu.lst file contents (both SATA drives are connected - Ubuntu is on SATA1 and XP is on SATA3 connectors in my PC).  Looking at the information below, it appears that the drive designation (hd0,1) or (hd1,0) is incorrect....??  should it be something like (sda0,1) and (sda1,0)...?
Here is the information...  

The command "sudo fdisk -l" returns:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris


Here are the "fstab" contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5fc1388-516d-4350-a0ea-14561c343699 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda5
UUID=debc0755-66fc-484d-a0b7-31196805b666 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0


And here are the "menu.lst" contents:

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
# rootnoverify	(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

title		WindowsXP
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

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
# kopt=root=UUID=c5fc1388-516d-4350-a0ea-14561c343699 ro
# kopt_2_6=root=/dev/sda1 ro

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by confused57 on 2007-04-17
I suppose you didn't have your Window's drive connected when you entered "sudo fdisk -l"...can you boot your Window's drive if you select it to boot first in bios?  Does bios recognize your hard drives correctly, when both drives are connected?  If I understand correctly, you can boot Ubuntu from grub with both drives connected.

I'm not sure where the problem lies, your grub Window's entry should work.

---

