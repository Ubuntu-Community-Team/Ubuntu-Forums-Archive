---
title: "Start Windows, and this GRUB thing"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by planemaniac on 2007-08-02
Hi,

I'm incredibly new to this, like, downloaded Ubuntu today. I installed it from the disc, and it told me to restart, and the disc ejected somewhere along the restart. It started up again, and I got this:

"GRUB Loading stage1.5.

GRUB loading, please wait...
Error 21"

And now I have absolutely no idea how to start Windows again, although, I can boot from the Ubuntu CD, but that doesn't do me any good as I now have a huge chunk of my hard drive missing due to the partiion, and no operating system to be seen!

Please help, thanks.

George.

---

### Post by LaRoza on 2007-08-02
What partitions are on the disk?

Use the live Cd, and type this command in the terminal

```

sudo df -l

```

Post the output here.

If you still have Windows, you can recover the MBR with the Super Grub Disk.

---

### Post by Hospadar on 2007-08-02
If you created a new partition to install linux on, you can enter your boot menu at startup (probably esc, F12, or del while the system is booting, before grub) and change your primary boot drive to the one that windows is installed on.

---

### Post by planemaniac on 2007-08-02
As far as I'm aware, there is only one partition, the one the Ubuntu installer made, and the remaining portion of the drive, which Windows controlled.

And this is the output from sudo df -l:

Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   127804     33788     94016  27% /lib/modules/2.6.20-15-generic/volatile
tmpfs                   127804     33788     94016  27% /lib/modules/2.6.20-15-generic/volatile
varrun                  127804       104    127700   1% /var/run
varlock                 127804         0    127804   0% /var/lock
udev                    127804        96    127708   1% /dev
devshm                  127804         0    127804   0% /dev/shm
tmpfs                   127804        12    127792   1% /tmp

Hope this helps somewhat.

Cheers, George.

---

### Post by philinux on 2007-08-02
If you have a start up disk boot from it and then fdisk mbr will sort out your windows install I'm pretty sure.

---

### Post by LaRoza on 2007-08-02
The out put was the file system of the live cd, not the hard disk, sorry.

Can you see the Windows partition at all?


If you can, get the Super Grub Disk, if you don't have the XP disk, to restore the MBR.

Or, you could install Ubuntu to the space made again. It will add XP to Grub.

---

### Post by LaRoza on 2007-08-02
> **philinux said:**
> If you have a start up disk boot from it and then fdisk mbr will sort out your windows install I'm pretty sure.

I thought it was "fixmbr"?

---

### Post by dannyboy79 on 2007-08-02
grub error 21 means that grub can't find the disk. so this means that you installed grub into the mbr of the disk that is being booted by the bios BUT it can't find the disk that has the kernel and grub's config files which are always located in /boot/grub/. please boot to a live cd and show me the output of these commands:

sudo fdisk -l

Sample output:
Disk /dev/hdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       36483   293049666    b  W95 FAT32 **(this is merely a file storage drive)**

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1          13      104391   83  Linux **(this is my /boot mount point)**
/dev/hdc2              14        1281    10185210   83  Linux **(this is my / mount point)**
/dev/hdc3            1282        1472     1534207+  82  Linux swap / Solaris **(swap)**
/dev/hdc4            1473        2434     7727265   83  Linux **(this is my /home mount point)**

now I need you to create a folder anywhere, then mount the / partition (IF you don't have a /boot partition and mount point) from the info you got from the fdisk command. Example would be the following:

mkdir /media/foo

then mount that / partition to the foo folder by issueing

sudo mount /dev/hdc2 /media/foo
(NOTE: you should change the /dev/hdc2 to whatever the output was from your fdisk command that is where your kernel and grub files were installed to and unless you choose to use /boot as it's own partition, than it'll be the same as /.)

now issue this command so we can see what your grub files are saying to mount

cat /media/foo/boot/grub/menu.lst

cat /media/foo/boot/grub/device.map

please post all teh output I ahve asked for and then I can help you.



this will give you your current location within the directory hierarchy. so it may be something like

---

### Post by dannyboy79 on 2007-08-02
> **philinux said:**
> If you have a start up disk boot from it and then fdisk mbr will sort out your windows install I'm pretty sure.

fdisk mbr from the windows xp recovery console will not sort everything out.

---

### Post by planemaniac on 2007-08-02
Right, I'm trying to change the boot drive before GRUB. So I press F12 I think it is, and I get given four options. Normal, Diskette, Hard-Disk Drive C: and IDE-CD-ROM Device. Which one would normal Windows be on. I tried Normal, and the GRUB thing came up again. I'm lost I have to say.

Cheers, George.

I just tried Hard-Disk Drive C: and the GRUB thing came up as well.

---

### Post by dannyboy79 on 2007-08-02
> **planemaniac said:**
> Right, I'm trying to change the boot drive before GRUB. So I press F12 I think it is, and I get given four options. Normal, Diskette, Hard-Disk Drive C: and IDE-CD-ROM Device. Which one would normal Windows be on. I tried Normal, and the GRUB thing came up again. I'm lost I have to say.

Cheers, George.

george, please provide the info I am asking for and I'll help you. please don't waste your time and reinstall any OS, this can be fixed!

updated: meant to say, don't reinstall any OS.

---

### Post by LaRoza on 2007-08-02
Grub is on the first sector of your hard drive. It cannot find an OS.

You can:

0. Reinstall Grub
1. Fix the MBR for Windows, if Windows is there, it will boot, and Ubuntu won't (if it is there).

---

### Post by philinux on 2007-08-02
:( Sorry if I got it wrong but on my millenium install this worked for me when I had error 21.

---

### Post by dannyboy79 on 2007-08-02
> **philinux said:**
> :( Sorry if I got it wrong but on my millenium install this worked for me when I had error 21.

you must be mistaken, ```
fdisk mbr 
``` wouldn't do anything. it will actually give you a invalid command.

I am pretty sure you meant to write
fixmbr

---

### Post by planemaniac on 2007-08-02
I get this from sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4862    39021885    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8502    68292283+   7  HPFS/NTFS
/dev/sdb2   *        8503       14853    51014407+  83  Linux
/dev/sdb3           14854       14946      747022+   5  Extended
/dev/sdb5           14854       14946      746991   82  Linux swap / Solaris

I create the /media/foo directory, I apparently successfull mount sda2, but when i try to open the menu.lst thing, it says No such file or directory. Oh dear!!

---

### Post by dannyboy79 on 2007-08-02
> **planemaniac said:**
> Sorry for PMing, I thought it would be easier this way. And the reason it's taking me so long is that i don't have interent on Ubuntu as it doesn't want to work so I'm having to transfer everything. Here is the output from sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 4 32098+ de Dell Utility
/dev/sda2 * 5 4862 39021885 7 HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 8502 68292283+ 7 HPFS/NTFS
/dev/sdb2 * 8503 14853 51014407+ 83 Linux
/dev/sdb3 14854 14946 747022+ 5 Extended
/dev/sdb5 14854 14946 746991 82 Linux swap / Solaris


And I tried mkdir /media/foo and I was told that it can't create directory because permission denied 

Please do not PM next time, it's better for everyone to see so that other's can benefit as well.

SO, it's just as I expected. You have 2 hard disks. Are you absolutely sure that windows is installed on the same disk as Ubuntu, which is /dev/sdb??? Please do the commands I said earlier but use sudo to create and mount the directory. I need to see the contents of your menu.lst file to help.

---

### Post by dannyboy79 on 2007-08-02
> **planemaniac said:**
> I get this from sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        4862    39021885    7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8502    68292283+   7  HPFS/NTFS
/dev/sdb2   *        8503       14853    51014407+  83  Linux
/dev/sdb3           14854       14946      747022+   5  Extended
/dev/sdb5           14854       14946      746991   82  Linux swap / Solaris

I create the /media/foo directory, I apparently successfull mount sda2, but when i try to open the menu.lst thing, it says No such file or directory. Oh dear!!

sda2 is NOT where linux is. Look at the System identifier column from the fdisk command. when you look down at each of the drives, where it says "Linux". that would be /dev/sdb2

---

### Post by philinux on 2007-08-02
It should have been fdisk /mbr

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

FDISK /MBR rewrites the Master Boot Record

---

### Post by planemaniac on 2007-08-02
Windows is installed on the 40GB drive, sda1 i believe. I created that directory, apparently mounted /dev/sda2 but when i tired to open menu.lst i was told no such file or directory. same with device.map.

---

### Post by dannyboy79 on 2007-08-02
> **philinux said:**
> It should have been fdisk /mbr

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

FDISK /MBR rewrites the Master Boot Record
ok, so we were both wrong. thanks for the info

---

### Post by dannyboy79 on 2007-08-02
> **planemaniac said:**
> Windows is installed on the 40GB drive, sda1 i believe. I created that directory, apparently mounted /dev/sda2 but when i tired to open menu.lst i was told no such file or directory. same with device.map.

GEORGE, slow down. Please read what I posted and perform what it says. I am trying to help you but you're not helping me help you.

You need to mount your /dev/sdb2 partition to that folder, then within /media/foo/boot/grub/ will be both files.

so which drive are you booting from the bios??? is it the 40gb or the other drive?

---

### Post by philinux on 2007-08-02
If you google fdisk mbr it also has links for xp equivalent

---

### Post by dannyboy79 on 2007-08-02
> **philinux said:**
> If you google fdisk mbr it also has links for xp equivalent

you specifically wrote that "fdisk mbr" fixed your computer which is didn't. DOS, linux, unix commands ALL are syntax critical. what you wrote would not work. that's all I was pointing out. Not to mention that MIcrosoft's own website for fdisk /mbr clearly states that it's applicable to everything PRIOR to winxp.

---

### Post by philinux on 2007-08-02
Hi Dannyboy,

what happened in my case was with 2 hard drives both got knackered. Grub failed with error 21 and the mbr on win me disk was knackered. fdisk /mbr sorted my machine out. then we disconnected the windows drive and re-istalled ubuntu. This sorted my problem out.
Only trying to help. Someone was right that fixmbr is for xp but I've never used xp . Thats why Im into Ubuntu.

---

### Post by planemaniac on 2007-08-02
I'm booting off the CD right now, Windows is on the 40GB I think, and Linux is on the 120GB I believe.

Here is what I get from menu.lst:

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
# kopt=root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro

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
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro single
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
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1



and device.map:

(hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by dannyboy79 on 2007-08-02
> **planemaniac said:**
> I'm booting off the CD right now, Windows is on the 40GB I think, and Linux is on the 120GB I believe.

Here is what I get from menu.lst:

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
# kopt=root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro

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
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=0d2ed3c2-900b-40c0-a6e3-1a1a6c8ffffa ro single
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
# on /dev/sda2
title           Microsoft Windows XP Professional
root            (hd0,1)
savedefault
makeactive
chainloader     +1



and device.map:

(hd0) /dev/sda
(hd1) /dev/sdb

you didn't answer me, which hard drive is being booted by the bios. please go into the bios and verify.
DId you swap around the disks at all or change anything after you installed Ubuntu?

---

### Post by planemaniac on 2007-08-02
How do I go into the BIOS? Sorry, I'm new to all this. And I've changed nothing at all in the computer.

---

### Post by dannyboy79 on 2007-08-02
if you don't mind, some questions can be answered if you would just take a moment and look for the answer yourself. I don't know what kind of computer you have and all computers are different. You need to gogle it OR just try hitting these keys immediately after you turn the computer on.

F1

Delete

F8

F10 or F11

I can't tell you but I am sure if you own a store bought pc like a dell or a compaq or whatever, it'll be on their support website.

---

### Post by planemaniac on 2007-08-02
Right, I think I've found what you're looking for. It's a Dell, and I did F2 at start up, scrolled down to Boot Sequence, number 1 is Diskette Drive, 2 Hard-Disk Drive C: and 3 IDE CD-ROM device. Hope this helps somewhat.

---

### Post by dannyboy79 on 2007-08-02
nope, not at all.

I am going to guess that your bios is booting up the sda1 disc and that you purchased the 120gb hard drive after the fact, installed it, and didn't change anything in the bios.

So what we need to do is reinstall grub and tell grub to look at your sdb hard drive for it's files. So this is how you do that.

Don't forget that this method, as described, puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root parititon. This is fine for most people, but not if you already have an alternative boot manager.

In other words, if you use something like Boot Magic or System Commander, the commands below will overwrite what you've got.

How to Restore Grub 

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "sudo -i"). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,1)" 
Use whatever your computer spits out for the following lines.

5. Type "root (hd1,1)".

6. Type "setup (hd0)". This will write GRUB to the MBR of your windows disk because that's what I beleive the bios is booting. 

7. Type "quit".

8. Restart the system. Remove the bootable CD.

This should get you into Ubuntu. We can work on windows from there. Also, don't worry, your windows install will be fine, it's merely writing to the first 412 or so bytes of the drive known as the master boot record.

---

