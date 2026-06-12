---
title: "How Do I Edit menu.lst?"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by drmsucks on 2007-05-14
Complete NOOB! But, I need to edit my menu.lst file in order to point to the correct partition to have Ubuntu show up in EasyBCD.  I have instructions for what to put in the file but how do I: a) find it, b) edit it?  Thanks.

---

### Post by taurus on 2007-05-14
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by 5-HT on 2007-05-14
Backup the old file:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```Open it up for editing:
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Dr Small on 2007-05-14
I don't know where your menu.lst is, but to edit things, you open the terminal and type
```
sudo gedit /path/to/menu.lst
```

Dr Small

---

### Post by JamieC on 2007-05-14
The GRUB menu.lst? Open a new terminal instance (Applications -> Accessories -> Terminal and type the following):
```

gksu gedit /boot/grub/menu.lst

```

Type your password when prompted and an editor will appear, allowing you to edit the file appropriately.

---

### Post by drmsucks on 2007-05-14
Thanks, but I need some path help.  I booted from the CD and need to edit the file on my Harddrive.  It shows up as "disk" but if I use the path: disk/boot/grub/menu.lst it's invalid.

---

### Post by taurus on 2007-05-14
If you boot it from a LiveCD, you need to mount / partition first before you can access or edit it.  Do you know which partition is /?  Otherwise, post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by 5-HT on 2007-05-14
Do you know what which partition it is (e.g., /dev/sda1)?

If so:
1. Mount the partition on your Desktop (replacing /dev/xxxx with the actual device)
```
mkdir ~/Desktop/linuxroot && sudo mount /dev/xxxx ~/Desktop/linuxroot
```2. Open up menu.lst from your root partition
```
sudo gedit ~/Desktop/linuxroot/boot/grub/menu.lst
```3.Save, and reboot
```
 sudo reboot 
```If not, have a look at 'sudo fdisk -l' to try and get an idea of what the partition may be getting recognized as.

HTH

---

### Post by drmsucks on 2007-05-14
System has 4 physical drives - Ubuntu is on (hd1,1) - sdb2 below.  What is correct path/syntax? Thanks

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
16 heads, 63 sectors/track, 144073 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      144071    72611752+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2   *       12749       38535   207134077+  83  Linux
/dev/sdb3           38536       38913     3036285    5  Extended
/dev/sdb5           38536       38913     3036253+  82  Linux swap / Solaris

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4500    36146218+   7  HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        4499    36138186    7  HPFS/NTFS

---

### Post by taurus on 2007-05-14
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sdb2 /mnt/ubuntu
gksudo gedit /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by drmsucks on 2007-05-14
Got it with your help!  But I need to investigate further - the changes I was told to make are already in the file.  Thanks very much.

---

### Post by taurus on 2007-05-14
What changes do you need to make to /boot/grub/menu.lst?  Post it here and the suggested changes.

```
cat /mnt/ubuntu/boot/grub/menu.lst
```

---

### Post by drmsucks on 2007-05-14
Thanks! Installed Ubuntu 7.04 today on drive that had Win Vista on it.  Install seemed to go ok.  Using EasyBCD to configure bootloader but it won't lead to a successful Linux boot. (The system currently dual boots Vista and XP.) Advice from EasyBCD forum was to edit menu.lst as follows:

"OK, now you need to change your menu.lst file to point to the right partition.

Something like this
default 0
timeout 0

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=d0002750-f7b3-4940-95e5-53663af009c9 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

where your root line says (hd1,1) though"

My menu.lst was as above except for the UUID.  My objective is to have all three OS show up on the same boot screen so that I can pick.  I need to get proficient in Linux so that I can tell MS to "kiss off" while they figure out which patents Linux has violated!  Thanks!

---

### Post by taurus on 2007-05-14
What is the layout of your harddrives?

```
sudo fdisk -l
```

---

### Post by drmsucks on 2007-05-14
I have 4 physical drives: C: - Win XP, D: - NTFS data drive, E: - NTFS Windows programs, and G: - Win Vista. The Linux partition is physically on G:.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
16 heads, 63 sectors/track, 144073 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 144071 72611752+ 7 HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 12748 102398278+ 7 HPFS/NTFS
/dev/sdb2 * 12749 38535 207134077+ 83 Linux
/dev/sdb3 38536 38913 3036285 5 Extended
/dev/sdb5 38536 38913 3036253+ 82 Linux swap / Solaris

Disk /dev/sdc: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 4500 36146218+ 7 HPFS/NTFS

Disk /dev/sdd: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 4499 36138186 7 HPFS/NTFS

---

### Post by drmsucks on 2007-05-15
BTW here's my menu.lst:

ubuntu@ubuntu:~$ cat /mnt/ubuntu/boot/grub/menu.lst
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
# kopt=root=UUID=bd0c9d54-5725-4a2b-a94f-b43a120153a0 ro

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
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bd0c9d54-5725-4a2b-a94f-b43a120153a0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=bd0c9d54-5725-4a2b-a94f-b43a120153a0 ro single
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
# on /dev/sdc1
title           Windows Vista/Longhorn (loader)
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title           Windows Vista/Longhorn (loader)
root            (hd3,0)
savedefault
makeactive
map             (hd0) (hd3)
map             (hd3) (hd0)
chainloader     +1

ubuntu@ubuntu:~$

---

