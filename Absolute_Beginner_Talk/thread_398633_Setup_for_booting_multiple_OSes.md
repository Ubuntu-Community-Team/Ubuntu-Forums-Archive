---
title: "Setup for booting multiple O/Ses?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by tomsyl on 2007-04-01
Apologies in advance if this is an obvious question, but I would like to have multiple versions of Linux available on my Pentium III-based computer (about 800 Mb of RAM) to try out and experiment with.  Specifically, I have Knoppix, Sabayon, Gentoo, and Red Hat Fedora 6, and likely will add more to that list. I currently have the system set up to dual boot either Ubuntu 5.06 or MS Windows XP; both OSes are on my C drive, which is evenly partitioned to give them about 35 Gb each. The computer also has an unpartitioned internal D drive with about 35 Gb of free space, but that could easily be increased to 60 Gb or more. I also have a 300 Gb USB 2.0 Seagate drive I use for backups that is currently not partitioned and has about 250 Gb free. (It is obviously slow due to the USB connection.)  Finally, I have a new, empty  Seagate 500 Gb "Mirra Personal Server" Network Drive that connects via an Ethernet cable to my wireless router.  I haven't tested it's transfer rate yet, but expect it to be fast due to the Ethernet connection.

I am obviously new here, and this might be too ambitious for a starter.  I have Ubuntu up and running reliably (though with some trouble with multimedia and screensavers I hope I'm capable of solving).  But my thinking is to leave Ubuntu and MS XP on the C drive, then set up the other operating systems in partitions on the D drive.  Ideally, I would get the BIOS screen I now get that gives me a brief period to select MS XP using the down-arrow key, then defaults to Ubuntu.*  The difference, of course, would that that BIOS boot screen would list the other Linux OS versions as well, which I could then select using the down-arrow key, just like I do now on the occasional time that I want to use MS Windows.

Is this feasible?  Is ther a certain order I should install the various Linux distros in?  What, if anything, do I need to do to get them each listed as a selection on that BIOS screen?  Will they share files, such as multimedia that's stored on the large external drives?

Thanks in advance for any help on this.  I've been having a great time with Ubuntu, and really enjoy the collaborative nature of the work you folks are doing.  There are very few things like this going on in the world today, and it's quite refreshing.

*As an aside, this screen lists Ubuntu three times and XP three times, as if there were six choices instead of two.  Why is that, and should I be worried?

---

### Post by seshomaru samma on 2007-04-01
If you install another version of Linux it will automatically recognise ubuntu and windows and would add them to the boot screen
if needed you can edit the boot screen at /boot/grub/menu.list ,but you shouldn't
at the moment you have ubuntu's boot menu (=brub)
but if you will install fedora then you will see fedora's boot screen , which will include ubuntu and windows

> As an aside, this screen lists Ubuntu three times and XP three times, as if there were six choices instead of two. Why is that, and should I be worried
can you post the output of this command :
> cat /boot/grub/menu.list

---

### Post by tomsyl on 2007-04-01
First, thank you for the help. Will that also happen with each successive distro installation (i.e., if I install Knoppix 5.1.1 or, say, GenToo after Fedora Core 6, will the subsequent distro always set itself up to boot as a default but the BIOS screen still give me an option to boot other, previously installed distros or MS Windows?

Second, I tried your inquiry by opening the terminal screen and posting

 cat /boot/grub/menu.list

after the ~$ and it returned 

No such file or directory

I tried again with the sudo prefix and still no luck.  Is this what you wanted me to do?  Or was this beginner's ignorance at work?

Finally, please excuse a delay in further responses - it's now 5:15 AM in Hawaii and I've been up all night experimenting with Ubuntu so I'm ready to pass out - a sure sign this stuff is addictive.  %^>

---

### Post by Austin_KW on 2007-04-01
type try cat /boot/grub/menu.lst

---

### Post by jvc26 on 2007-04-01
The fact that grub doesnt appear to be there is interesting - does the file exist (moving either through cd commands in terminal or more simply via nautilus - see if there is a /boot/grub/menu.lst
From my own experience a fair few distros just recognise what is on the drive already and adds them to its bootloader (NOT THE CASE WITH XP Microsoft Bootloader - which refuses to recognise anything but itself) That isnt guaranteed, but if you know where the partitions are and where they store their boot info then you can always add them into GRUB later.
Il

---

### Post by confused57 on 2007-04-01
You might want to check out this website:
[http://www.ubuntuforums.org/showthread.php?t=398633](http://www.ubuntuforums.org/showthread.php?t=398633)

See the section on grub, which has a section for booting multiple Linux OS.
The section on "Mounting Filesystems" explains how to mount various filesystems(ext3, NTFS, FAT,etc)...this enables you to access the partitions in Linux.

You can install this driver in Windows, which enables Windows to recognize & access ext3 partitions:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by tomsyl on 2007-04-01
> **Austin_KW said:**
> type try cat /boot/grub/menu.lst

That worked - this is the reply:

<<<<<<<<<<<text from terminal begins>>>>>>>>>>>>>>>>>

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
# kopt=root=/dev/hdb2 ro

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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1


<<<<<<<<<<<<<<<<<<<text from terminal ends>>>>>>>>>>>>>

Please note that I only installed Ubuntu once; however, I did run it from the liveCD for a while before installing it. 

As an aside, should I save that password for some reason?

 Thank you.

---

### Post by seshomaru samma on 2007-04-01
sorry it was lst not list
If you look carefully at the different Ubuntu option you will notice that the number is not the same
thats because you installed an update which included a new kernel ,so in the boot menu you get an option to load Ubuntu with the new kernel and the old kernel
if your new kernel is working ok you can comment out the old one by putting a # infront of it
like this , 
look for this line:
```
title Ubuntu, kernel 2.6.15-23-386
root (hd1,1)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot
```
and change it to:
```
#title Ubuntu, kernel 2.6.15-23-386
#root (hd1,1)
#kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hdb2 ro quiet splash
#initrd /boot/initrd.img-2.6.15-23-386
#savedefault
#boot
```
you can do the same for the recovery option (but dont comment out the new kernels recovery mode)

as for XP noitice that you have a different boot directory in each option
hd0,0
hd1,0
hd2,0
in order to know which one you need you need to post the output of
```
sudo fdisk -l
```

---

