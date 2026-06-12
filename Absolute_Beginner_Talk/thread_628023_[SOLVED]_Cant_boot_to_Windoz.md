---
title: "[SOLVED] Cant boot to Windoz"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by caoinan on 2007-11-30
I just recently installed openSUSE and I have several other linux distros on my computer, but after I installed SuSE I couldnt boot into windoz. I know this isnt alot of information but if you tell me what else you need to know I will try to get it. I think it just doesnt know where to look for it and i've tryed copying Ubuntu's grub menu.lst for windoz and it didnt work

---

### Post by jken146 on 2007-11-30
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)  edit: That's not what you want, sorry.

---

### Post by Duck2006 on 2007-11-30
Type

sudo fdisk -l

and

cat gedit /boot/grub/menu.lst

and post the output hear.

---

### Post by teryowen on 2007-11-30
well im not sure if you realize but this is called "_Ubuntu _Forums" thought i point it out.

But ill help anyways.

OpenSUSE useally installs a GRUB loader?

So when you boot up do you see a menu where you can choose SUSE or windows?

If not go into terminal run:

grub
root (hd0,0)     <--- partition of linux (if its 1 then hd0,0 if its 2 then hd0,1 if its 3 the hd0,2 if its on another hard drive it would be hd0,0 and so on)
setup (hd0)
quit

---

### Post by caoinan on 2007-11-30
I do see where it says windoz but when I choose it, it goes to a black screen that says one or two lines from the grub menu.lst

---

### Post by caoinan on 2007-11-30
keenan@keenan-desktop:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf65af65a

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9327    74919096   83  Linux
/dev/hda2            9328        9729     3229065    5  Extended
/dev/hda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8883070

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13316   106960738+   7  HPFS/NTFS
/dev/sda2           13317       17519    33760256+  83  Linux
/dev/sda3           17520       21538    32282617+  83  Linux

-------------------------------------------

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=14a88df4-4c03-4a67-a730-8fe3dc5962d1 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title MEPIS at sda2, newest kernel
root (hd1,1)
kernel /boot/vmlinuz root=/dev/sda2 nomce quiet vga=791 
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

keenan@keenan-desktop:~$

---

### Post by Duck2006 on 2007-11-30
Do you have a sata and a pata drive?

you can try reinstalling grub again.

in the terminal type

sudo grub

then at the grub promp type

find /boot/grub/stage1

it will came back with some thing like (hd0,0) and (sd0,0) so in the next step use the ubuntu linux

root (sd0,0)

setup (sd0)

quit

and then reboot the system

---

### Post by caoinan on 2007-11-30
here is what is says when i try to boot into windoz and to the guy saying this is a ubuntu for i have ubuntu for several months now but i just wanted to try some other distros, i now have ubuntu, mepis, openSuSE, and Windows XP(on seperate harddrive).

rootnoverify (hd1,2)
chainloader (hd1,0) +1

---

### Post by Duck2006 on 2007-11-30
> rootnoverify (hd1,2)
chainloader (hd1,0) +1

This should read this

> 
rootnoverify (hd0,0)
chainloader  +1

Thats if the linux install is on the same drive as windoze and the boot drive that you are using.

---

### Post by caoinan on 2007-11-30
I have all of my Linux distros on a seperate harddrive from windoz
windoz looks like this in my grub should i change any of it

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by Duck2006 on 2007-11-30
It you go into your BOIS and change it to boot from the windoze drive does windoze boot?
If not use the windoze cd to fix the mbr of the windoze drive and the change to the ubuntu drive and see if windoze boots from that.

---

### Post by caoinan on 2007-11-30
yes it works when I switch to that drive just not from grub

---

### Post by Duck2006 on 2007-11-30
Ok cool, then change back to the drive you had befor, and you have to install grub from the linux that you booted windoze from befor you installed suse from and you can add the suse line to it and you can run all your installs then.

witch should be 

root (hd0,0)
setup (hd0)

---

### Post by caoinan on 2007-11-30
ok what take the line from SuSE and add it to ubuntu is that what your saying or vice versa

---

### Post by sandysandy on 2007-11-30
> **caoinan said:**
> ok what take the line from SuSE and add it to ubuntu is that what your saying or vice versa

have u tried the Super Grub Disk

regards

---

### Post by Duck2006 on 2007-11-30
If suse is on your pata sata drive and you are booting from the pata drive then you have to edit the menu.lst on you ubuntu drive bye adding the lines from suse to it for suse to boot. You will have to mount your suse partition in ubuntu

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

then look at /boot/grub/menu.lst and see what you have to copy to your ubuntu menu.lst to boot suse.

---

### Post by caoinan on 2007-11-30
no suse, ubuntu, and mepis all boot fine just windoz doesnt. And ive never used super grub disk do i have to install it

---

### Post by sandysandy on 2007-11-30
> **caoinan said:**
> no suse, ubuntu, and mepis all boot fine just windoz doesnt. And ive never used super grub disk do i have to install it

Super Grub Disk (SGD for short) is an utility which u can download and then burn a bootable CD.  after u boot into SGD, it lets u fix the Master Boot Record. it can help u fix Linux issues as well by helping to reinstall GRUB correctly.

the link is

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

regards

---

### Post by Duck2006 on 2007-11-30
Witch  menu.lst that you are booting the linux systems from?
Is it the suse?

---

### Post by caoinan on 2007-11-30
> **Duck2006 said:**
> Witch  menu.lst that you are booting the linux systems from?
Is it the suse?

yes it is suse now and everything was working until i installed suse and everything is except for windoz and i tryed adding ubuntus menu.lst lines for windoz to suse but that didnt work either

---

### Post by sandysandy on 2007-11-30
> **caoinan said:**
> yes it is suse now and everything was working until i installed suse and everything is except for windoz and i tryed adding ubuntus menu.lst lines for windoz to suse but that didnt work either

i had a similar problem after i installed Mandriva. Only thing was that the Win XP was detected but Open SUSE and Ubuntu were not in the bootable options. So i copied the relevant portions of the Mandriva booting sequence and pasted them into the ubuntu menu.lst, after restoring grub of ubuntu using Super Grub Disk. after i restarted the computer i got all options.

regards

---

### Post by caoinan on 2007-11-30
ok hopefully I can get it working I just finished burning it I'll let yall know if it works for me or not

---

### Post by Duck2006 on 2007-11-30
Ok then in the menu.lst from suse try

title womdoze
root(sd0,0)
chainloader +1

or it will be

title windoze
root (sd1,0)
map (sd0) (sh1)
map (sd1) (sd0)
chainloader +1

---

### Post by caoinan on 2007-11-30
ok I got it working thanks alot everyone

---

