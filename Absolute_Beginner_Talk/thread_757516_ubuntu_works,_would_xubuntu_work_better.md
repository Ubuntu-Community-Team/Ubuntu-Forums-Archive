---
title: "ubuntu works, would xubuntu work better?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by etnyide on 2008-04-17
I am using a dell inspiron 2650 with a celeron 1.2 or 1.5 with 512 mb of ram.

With that said, this computer is about 80% internet appliance.

Windows had become so bogged with spyware etc that I reformatted the hard drive and started clean. I went to Ubuntu after unsuccessfully trying several other live CD's. As a side note, I am amazed at the quality and fit and finish of Ubuntu. Thanks to all for providing a quality solution. I reinstalled windows for the occasional need for autoCAD and Sketchup but I have not allowed windows on the internet. 

Questions:

The system will not boot either OS by default. If the Ubuntu CD is in the drive, I see the grub (?) menu and can boot to either OS. Once the grub menu appears, the CD can be removed and the computer will boot either OS. What do I need to do to remove this annoying step of having the CD in the drive just to boot?

Would I see a dramatic improvement by switching to Xubuntu? Firefox and open office and yes those addictive games are all I use Ubuntu for. 

This is a windows user speaking. Do I need to be running any sort of anti-spyware type software under Ubuntu? 

Ubuntu is telling me there are 200 updates available. I tend to follow the motto "if it works, don't fix it" Do I need all those 200 updates?

Simple answers please? I am novice and have no interest in learning what goes on under the gui and hope to never have to use the command line! Figuring out how to get the wireless security key into Ubuntu was as technical as I care to get. I want to keep it simple and streamlined as much as possible.

Again, thanks to all for the answer to keeping an old laptop useful!

---

### Post by SnakeHips on 2008-04-17
Xubuntu may be a little lighter on your hardware than Ubuntu ,i've used both and have xubuntu installed at the moment ;-) What version are you using 7.10?

...and welcome ,enjoy your stay.

---

### Post by martrn on 2008-04-17
> The system will not boot either OS by default. If the Ubuntu CD is in the drive, I see the grub (?) menu and can boot to either OS. Once the grub menu appears, the CD can be removed and the computer will boot either OS. What do I need to do to remove this annoying step of having the CD in the drive just to boot?
It order to boot both OS's you would need to install Grub to the MBR (master boot record) of the hard drive.  Usually ubuntu will ask you if you wish to do this during install, eg it will stay do you wish to install Grub the linux/ubuntu boot loader to the MBR of hard drive /hda or catution over-righting your master boot record..... etc...ect...  Some people get put off by this warning but grub is a solid boot loader, and can boot multiple operating systems for windows, solaris to the whole range of linux systems, and it is perfectly ok to install grub to your master boot record.  You have many options to boot either os, but all will require configering a boot loader, of some kind, but grub would probebly be the best.  Some anti-virual proof mother boards will prevent you installing or over-righting the MBR (master boot record).

> Would I see a dramatic improvement by switching to Xubuntu? Firefox and open office and yes those addictive games are all I use Ubuntu for.
If you can run open office then usinging Xubuntu / Kubuntu / Gnomes-ubuntu is a matter of personal choice, I prefer Kubuntu, its cool, and I would reccomend that but it is still a matter of choice.  You can install (from a terminal)
```
 sudo apt-get update
 sudo apt-get install kubuntu-desktop
 sudo apt-get install xubuntu-deskto
```
and try the kde desktop and when you login change the defualt start session and see if it is better for you.

> This is a windows user speaking. Do I need to be running any sort of anti-spyware type software under Ubuntu? 
Not really just never run as root or log-in as root, and be carefull which reposotories you add to your sources list, and if you install .deb files through the debian installer be careful where you get the .debs from.

> Ubuntu is telling me there are 200 updates available. I tend to follow the motto "if it works, don't fix it" Do I need all those 200 updates?
Yes you need to install them, some of them will be security patches.  

> Simple answers please? I am novice and have no interest in learning what goes on under the gui and hope to never have to use the command line! Figuring out how to get the wireless security key into Ubuntu was as technical as I care to get. I want to keep it simple and streamlined as much as possible.
The command line is cool, you need to find your way around a terminal or at the least be a little comptable with it.  Its really not that scary.  Its just a terminal.

---

### Post by etnyide on 2008-04-17
I am not sure which version I am running!

I downloaded the iso about a month ago.

where can you see what version you are running?

does it have an "about this mac" or "my computer properties" hidden somewhere?

I suspect that performance within firefox is affected more by the weather and my dsl provider than ubuntu vs xubuntu.

---

### Post by martrn on 2008-04-17
> I am not sure which version I am running!I downloaded the iso about a month ago. where can you see what version you are running? does it have an "about this mac" or "my computer properties" hidden somewhere?

Menu >> Settings >> System Monitor
Should tell you somebasic information about what version you are running as well as a resources tab to check your system performance and what processes you are running.  You can see how far streached your system is from here also.

> I suspect that performance within firefox is affected more by the weather and my dsl provider than ubuntu vs xubuntu.

Welcome to ubuntu !!

---

### Post by SnakeHips on 2008-04-17
Would you post the output

```
gedit /boot/grub/menu.lst
```

and 

```
sudo fdisk -l
```
note: this is NOT like windows it does'nt format your disk ,merely displays info.

....so we can see what OS you have installed and how the partitions are set.

---

### Post by SunnyRabbiera on 2008-04-17
> **martrn said:**
> Menu >> Settings >> System Monitor
Should tell you some basic information about what version you are running as well as a resources tab to check your system performance and what processes you are running.  You can see how far streached your system is from here also.



Welcome to ubuntu !!

Yup, the system monitor should give you the info you need in the first tab.

---

### Post by Oldsoldier2003 on 2008-04-17
```
cat /etc/lsb-release
``` will tell you the release

---

### Post by oldos2er on 2008-04-17
I don't think there is any anti-spyware software for Ubuntu, other than a couple rootkit checkers.

 You should install the security updates.

---

### Post by stchman on 2008-04-17
> **etnyide said:**
> I am using a dell inspiron 2650 with a celeron 1.2 or 1.5 with 512 mb of ram.

With that said, this computer is about 80% internet appliance.

Windows had become so bogged with spyware etc that I reformatted the hard drive and started clean. I went to Ubuntu after unsuccessfully trying several other live CD's. As a side note, I am amazed at the quality and fit and finish of Ubuntu. Thanks to all for providing a quality solution. I reinstalled windows for the occasional need for autoCAD and Sketchup but I have not allowed windows on the internet. 

Questions:

The system will not boot either OS by default. If the Ubuntu CD is in the drive, I see the grub (?) menu and can boot to either OS. Once the grub menu appears, the CD can be removed and the computer will boot either OS. What do I need to do to remove this annoying step of having the CD in the drive just to boot?

Would I see a dramatic improvement by switching to Xubuntu? Firefox and open office and yes those addictive games are all I use Ubuntu for. 

This is a windows user speaking. Do I need to be running any sort of anti-spyware type software under Ubuntu? 

Ubuntu is telling me there are 200 updates available. I tend to follow the motto "if it works, don't fix it" Do I need all those 200 updates?

Simple answers please? I am novice and have no interest in learning what goes on under the gui and hope to never have to use the command line! Figuring out how to get the wireless security key into Ubuntu was as technical as I care to get. I want to keep it simple and streamlined as much as possible.

Again, thanks to all for the answer to keeping an old laptop useful!

Ubuntu will run fine with those specs.  My laptop is a Celeron 1.73 with 512MB RAM and it runs great.  I upgraded to 1GB RAM, but saw near zero performance gain.

Yers, install the updates.

For wireless, what kind of wireless card do you have?

Post an lspci terminal output here in this thread.

---

### Post by Melk79 on 2008-04-17
Just to be clear... you did do a full install after you originally booted Ubuntu from the LiveCD?

Also, keep an eye on Google because they already have Google Earth and Picasa for Linux and may be adding Sketch Up soon.  One less reason for Windows.

---

### Post by LowSky on 2008-04-17
Fiefox can be edited to do something better if you enable them, go to google and type firefox hacks

---

### Post by arashiko28 on 2008-04-17
You have the 200 updates pending because of the date, you downloaded 7.10 which is still good and the latest version until (let's pray) April 25th, when the LTS 8.04 version comes out to our hands. I have xubuntu on a celeron coppermint at 733mHz, 384MB RAM and works like a charm.

Welcome to the Linux family!!! You'll be surprised of how many things you can do with Ubuntu.

---

### Post by etnyide on 2008-04-17
Ok, so I looked at the system monitor and it is 1.5 celeron and 256mb of ram.

The wireless card is a 

d-link airplus G 
dwl-g630

ubuntu did a wonderful job finding it. 

Suggestion. Ubuntu should take a hint from OSX in regards to finding wireless sites. It should be a drop down menu on the top bar. I am at the library and did figure out how to connect here but it should have been more intuitive. Listen to me already critiquing this thing and I have been using it less than a week!

Running Ubuntu Release 7.04 (feisty)

load averages says 0.93, 0.51, 0.53

gimp, and oo spreadsheet, file browser to my usb jump drive, firefox, and system monitor are all running.

OK, so I found the terminal. It feels like I'm back in high school running DOS again.
(I so just dated myself)

the result of 

gedit /boot/grub/menu.lst

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
# kopt=root=UUID=f9406433-1066-4cc8-b0d9-dfbd9550bc2b ro

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
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f9406433-1066-4cc8-b0d9-dfbd9550bc2b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f9406433-1066-4cc8-b0d9-dfbd9550bc2b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.20-15-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f1ccc5e8-4472-405b-ad2e-7971758a6628 ro quiet splash 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f1ccc5e8-4472-405b-ad2e-7971758a6628 ro single 
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Ubuntu, memtest86+ (on /dev/sda3)
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot


Here is the result of 

sudo fdisk -l


steve@steve-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3226    25912813+   7  HPFS/NTFS
/dev/sda2            6211        7295     8715262+   f  W95 Ext'd (LBA)
/dev/sda3            3227        4748    12225465   83  Linux
/dev/sda4   *        4749        6210    11743515   83  Linux
/dev/sda5            6375        7295     7397901    e  W95 FAT16 (LBA)
/dev/sda6            6282        6374      746959+  82  Linux swap / Solaris
/dev/sda7            6211        6281      570244+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1019 MB, 1019215872 bytes
16 heads, 63 sectors/track, 1974 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1975      995296+   e  W95 FAT16 (LBA)
steve@steve-laptop:~$ 



Here is the result of 

lspci

steve@steve-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
steve@steve-laptop:~$ 


Does all of that make sense?

---

### Post by etnyide on 2008-04-17
Sketchup for linux would be awesome! Then AutoCAD would be the only remaining reason to keep windows on the computer.

---

### Post by etnyide on 2008-04-17
Melk 79

To clarify, I did do a full install. 

Once I see the grub menu, I can remove the cd and boot to either OS just fine.

---

### Post by crjackson on 2008-04-17
> **etnyide said:**
> Melk 79

To clarify, I did do a full install. 

Once I see the grub menu, I can remove the cd and boot to either OS just fine.

It seems like your installed Ubuntu 1st and then later installed windows.  I suspect that the windows install stole your MBR and that's why you don't have a GRUB MBR.

Just a guess on my part.  Either way, you need to install those updates and you need to re-install GRUB.

---

