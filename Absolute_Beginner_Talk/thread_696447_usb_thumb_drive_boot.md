---
title: "usb thumb drive boot"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by warrior24 on 2008-02-14
I am having trouble with this command while trying the turitol listed below
sudo mount ubuntu-7.10-desktop-i386.iso -o loop /media/ubuntu_iso


it says No such file or directory


[http://ubuntuforums.org/showthread.php?t=575406](http://ubuntuforums.org/showthread.php?t=575406)

---

### Post by marufaberlin on 2008-02-14
Are you in the directory where the iso file is? If not, cd there.
Does the folder /media/ubuntu_iso exist?

---

### Post by warrior24 on 2008-02-14
Ok I cd into it now got past that part thanks. However

 I am stuck on 

grub> root (hd1,0)

But mine looks like  but it errors

grub> find /boot/grub/menu.lst 
 (hd0,0)
 (hd0,8)
 (hd2,0)

grub> geometry (hd0)
drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/hda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x7
   Partition num: 7,  Filesystem type unknown, partition type 0x82
   Partition num: 8,  Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd2)
drive 0x82: C/H/S = 244/255/63, The number of sectors = 3928064, /dev/sdb
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type is ext2fs, partition type 0x83

grub> grub> root (hd2,0)

Error 27: Unrecognized command

grub>

---

### Post by warrior24 on 2008-02-14
Ok I got past all that but when I boot of the thumb drive and try to boot off of the options i get Error 15 file not found the only on that seems to work is the super grub disk part.

---

### Post by warrior24 on 2008-02-14
kernel (hd0,0) /casper/vmlinuz file=cdrom/preseed/ubuntu.seed boot=casper quiet splash --
Error 15: File

press any key to continue ...

---

### Post by adrian15 on 2008-02-14
Did you edit manually the menu.lst file?

Can you copy-paste your menu.lst?

Are you sure that when you open the pendrive you see the casper folder... did you perhaps copy it inside another folder?

adrian15

---

### Post by warrior24 on 2008-02-14
LOL I did copy paste I noticed it did say adrian15 and I was like wow how did it know my name but then I realized that it was some one else (you) should I edit it since I am using fluxbuntu? 

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#Thank you adrian15!
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
usbshift

#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.

default 0
#timeout 2
setgrubdevice # This is compulsory
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
#gfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan

title       Ubuntu Gutsy Gibbon in Persistent Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper persistent quiet splash --
initrd    $(grub_device)/casper/initrd.gz

title       Super Grub Disk
configfile $(grub_device)/boot/sgd/menu.lst

title      Ubuntu Gutsy Gibbon in Live CD Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd   $(grub_device)/casper/initrd.gz 

title       Start Ubuntu in Safe Graphics Mode
kernel   $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper xforcevesa quiet splash --
initrd    $(grub_device)/casper/initrd.gz 

title        Install with Driver Update CD
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true quiet splash --
initrd     $(grub_device)/casper/initrd.gz 

title        OEM Ubuntu Gutsy Gibbon Install (for manufacturers)
kernel    $(grub_device)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper oem-config/enable=true quiet splash --
initrd     $(grub_device)/casper/initrd.gz 

title        Check CD for Defects
kernel    $(grub_device)/casper/vmlinuz boot=casper integrity-check quiet splash --
initrd      $(grub_device)/casper/initrd.gz 

title        Memory Test
kernel    $(grub_device)/install/mt86plus  - 

title       Boot the First Hard Disk
root       (hd0)
chainloader +1

title       Boot the Second Hard Disk
root      (hd1)
chainloader +1

---

### Post by adrian15 on 2008-02-14
> **warrior24 said:**
> LOL I did copy paste I noticed it did say adrian15 and I was like wow how did it know my name but then I realized that it was some one else (you)
It's me :).
> **warrior24 said:**
> 
 should I edit it since I am using fluxbuntu? 
I actually do not know how does fluxbuntu call its kernel. You should try to see in your pendrive which are the files founds in the casper folder to see if there is something like vmlinuz-2.6.20 or initrd-2.6.20 or something like that and just edit menu.lst accordingly.

adrian15

---

### Post by warrior24 on 2008-02-14
I see nothing in the casper-rw but in ubuntu710 i see

---

### Post by adrian15 on 2008-02-14
> **warrior24 said:**
> I see nothing in the casper-rw but in ubuntu710 i see

The kernel and initrd files should be found inside the isolinux folder. Either you create a casper file and you copy both files in this folder or you edit menu.lst with the isolinux path in mind.

However it does mean that everything is going to work. It seems that Fluxbuntu live cd is quite different from Ubuntu Live cd.

If you modify menu.lst do not forget to copy-paste here your changes to us to check if there is anything wrong.

adrian15

---

### Post by warrior24 on 2008-02-14
ill try again with ubuntu this time.

---

