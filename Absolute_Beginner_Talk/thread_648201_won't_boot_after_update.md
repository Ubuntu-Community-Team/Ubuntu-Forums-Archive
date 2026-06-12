---
title: "won't boot after update"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by axamax on 2007-12-23
I just restarted after the update manager updated a few things. I think the kernel was one of the items. I can't boot beyond the grub menu now? Latest Kernel 2.6.22.14
Any ideas?
Error message as follows::

[      21.017269] crc error
[      21.018569] KERNEL Panic- not syncing: VFS: Unable to mount fs on unknown block (0,0)

---

### Post by axamax on 2007-12-23
help!

---

### Post by PmDematagoda on 2007-12-23
Boot one of the older kernels, then post the results of:-
```

sudo fdisk -l
```
and
```
cat /boot/grub/menu.lst
```

---

### Post by axamax on 2007-12-23
As Requested

ubuntu@ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x307a307a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       20022   160826683+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005e663

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38536   309540388+  83  Linux
/dev/sdb2           38537       38913     3028252+   5  Extended
/dev/sdb5           38537       38913     3028221   82  Linux swap / Solaris
ubuntu@ubuntu-desktop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu 7.10, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet

title           Ubuntu 7.10, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

ubuntu@ubuntu-desktop:~$ 
ubuntu@ubuntu-desktop:~$

---

### Post by PmDematagoda on 2007-12-23
Your menu.lst looks good, may I ask how Update Manager gave you kernel 2.6.22 as an update? Usually Ubuntu does not upgrade the kernel within a release, for example, Feisty will always have 2.6.20 and Gutsy will always have 2.6.22, of course you can upgrade the kernel using other ways.

---

### Post by axamax on 2007-12-23
may not have been the kernel but it updated 12 items today i thought the kernel was one of them.

---

### Post by PmDematagoda on 2007-12-23
Could you post the result of:-

```
cat /etc/apt/sources.list
```

---

### Post by axamax on 2007-12-23
ubuntu@ubuntu-desktop:~$ sudo cat /etc/apt/sources.list
[sudo] password for ubuntu:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
ubuntu@ubuntu-desktop:~$

---

### Post by PmDematagoda on 2007-12-23
Could you post the result of:-

```
cat /etc/lsb-release
```

It seems to me that your sources.list file is messed up, but whether the mess-up is big or not, we shall see.

---

### Post by axamax on 2007-12-23
ubuntu@ubuntu-desktop:~$ sudo cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
ubuntu@ubuntu-desktop:~$

---

### Post by PmDematagoda on 2007-12-23
Open the sources.list file for editing using:- 

```
sudo gedit /etc/apt/sources.list
```

Then remove these lines:-
```
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

Save the file and do:-
```

sudo apt-get update
```

But concerning your kernel error, I do not know why you should be getting it since the menu.lst is correct.

---

### Post by axamax on 2007-12-23
Done those I'll have a go at rebooting now.

---

### Post by axamax on 2007-12-23
Still getting the same error when I try to boot

---

### Post by axamax on 2007-12-23
Is there anything like System Restore on Gutsy?

---

### Post by zero-9376 on 2007-12-23
i would maybe try reinstalling the latest kernel through synaptic and initrd-tools based on this thread: [http://ubuntuforums.org/showthread.php?t=27709](http://ubuntuforums.org/showthread.php?t=27709)

by the way you dont need system restore you already have the older kernel that works on your system, until you can figure this out you can use that one

---

### Post by axamax on 2007-12-23
initrd-tools doesn't seem to be available. Has it perhaps been renamed or superceded

---

### Post by Philip Hosmer on 2007-12-23
Axamax,
I had the same trouble after update here is the grub list - I am absolute beginner. I had the grub loader not found on restart & I lost all but the main drives - maybe more, Can you check this over for me? Ihave Feisty fawn.
Philip Hosmer

phosmer3@phosmer3-basement:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=e72d2a3c-2989-4237-a737-26da3df91e5e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e72d2a3c-2989-4237-a737-26da3df91e5e ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=e72d2a3c-2989-4237-a737-26da3df91e5e ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e72d2a3c-2989-4237-a737-26da3df91e5e ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e72d2a3c-2989-4237-a737-26da3df91e5e ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

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

phosmer3@phosmer3-basement:~$

---

### Post by Philip Hosmer on 2007-12-23
Now after a couple of reboots all seems fine. I have no idea what happened but all seems to be in order. HaHa appy.
Thanks

---

### Post by meierfra on 2007-12-23
axamax: post the output of 

```
sudo blkid
```

Maybe your UUID's got messed up.

---

### Post by philinux on 2007-12-23
Someone else had similar. You dont mention a grub error so this might not be the same.

[http://ubuntuforums.org/showthread.php?t=645116](http://ubuntuforums.org/showthread.php?t=645116)

---

### Post by axamax on 2007-12-24
ubuntu@ubuntu-desktop:~$ sudo blkid
[sudo] password for ubuntu:
/dev/sda1: TYPE="ntfs" UUID="10109739109724AE" 
/dev/sdb1: UUID="60aa0ef0-121f-478e-a90c-c229d150e290" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8006153e-b160-458a-902f-e72666e423ee" 
ubuntu@ubuntu-desktop:~$

---

### Post by PmDematagoda on 2007-12-24
Your UUID looks different, when you reach the GRUB list, press "E", then scroll down to the second line and press "E" again, change the line from:-

```
kernel /boot/vmlinuz-2.6.20-16-generic root=**[COLOR="Red"]UUID=e72d2a3c-2989-4237-a737-26da3df91e5e[/COLOR]** ro single
```
to:-
```
kernel /boot/vmlinuz-2.6.20-16-generic root=**[COLOR="Red"](hd1,0)[/COLOR]** ro single
```
After the change is done, press Enter and then press "B", see if your problem is solved.

---

### Post by axamax on 2007-12-24
Tried this but it didn't seem to work.
I might not be doing it right. When i go to edit it I have other info appear and the cursor is directly at the end of the line. I added the line "Kernel.......(hd1,0) ro single" and it said unknown command.

I have to go now I'd appreciate continuing with this on Thursday.

Thanks

---

### Post by PmDematagoda on 2007-12-24
Don't add a line, you should edit the second line after the entry for root.

---

### Post by meierfra on 2007-12-24
Use "root=/dev/sdb1"  not "root (hd1,0)"

The kernel line parameters are   read by the kernel (not by grub). (hd1,0) is grub speak, the kernel won't understand it.

---

### Post by meierfra on 2007-12-25
Sorry, I didn't have much time earlier today and hadn't compared the UUID's  in menu.lst and blkid. They actually match. So changing "root=UUID=...." to "root=/dev/sdb1" mostly likely will not solve your problem.

Lets see whether you can access your Ubuntu partition  from the LiveCD. Boot from the LiveCD, open a terminal and  type

```

mkdir ubuntu
sudo mount -t ext3 /dev/sdb1 ubuntu
```

If you get an error message, post it here.

---

### Post by PmDematagoda on 2007-12-25
meierfra the blockID's actually differ:-
Result of blkid:-
```
/dev/sdb1: UUID="**[B][COLOR="Red"]60aa0ef0-121f-478e-a90c-c229d150e290[/COLOR]**[/B]"
```
Menu.lst:-
```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=**[COLOR="Red"]e72d2a3c-2989-4237-a737-26da3df91e5e[/COLOR]** ro quiet splash
```
So if the menu.lst entry was changed, that would solve the problem.

---

### Post by meierfra on 2007-12-25
PmDematagoda:  You are comparing axamax blkid with  Philip Hosmer menu.lst. Of course they won't match.

---

### Post by PmDematagoda on 2007-12-25
Sorry, but then how do you make a blkID for GRUB's menu.lst file?

---

### Post by meierfra on 2007-12-25
> Sorry, but then how do you make a blkID for GRUB's menu.lst file?
??????

axamax also posted his/her  menu.lst.[  (post 4) ]("http://ubuntuforums.org/showthread.php?t=648201#4") It  contains the same UUID as the blkid. So there is no problem with UUIDs.

---

### Post by PmDematagoda on 2007-12-25
My goodness, what a mistake I made:oops:, and there I was thinking something even more stupid about blkID's. Thank you for correcting me meierfra, I was half on my way to the North Pole the way I was going with the thread#-o.

But there is no necessity in ensuring the consistency of the root since the OP was able to boot one of the older kernels properly. So there must be something else.

Looking back, I see that the thread has been really messed up.

Now it has been established that the OP(axamax):-
1) Upgraded Ubuntu.
2) Can boot the older kernels.
3) His menu.lst is fine.

So we can build on that.

---

### Post by PmDematagoda on 2007-12-25
Maybe, as suggested previously, the OP can remove the kernel and reinstall it to see if it was something with the kernel or something else.

---

### Post by meierfra on 2007-12-25
I don't think axamax has an older kernel to  boot from.  He/she seems to be booting from the LiveCD:

> ubuntu@ubuntu-desktop

---

### Post by PmDematagoda on 2007-12-25
Yes, yet....according to what he/she says on his 4th post, he seems to be using the older kernel as I suggested earlier. But it is rather difficult to ensure that this is the case without the OP himself, so we will have to wait until the OP clarifies it before deciding what should be done next.

axamax, on your 4th post, did you boot another, older kernel, or did you boot the Live CD?

---

### Post by axamax on 2007-12-27
sorry for the delay. I got dragged away for xmas
. I have been having to boot from an earlier kernel in recovery mode.

---

### Post by meierfra on 2007-12-27
I have seen some people solve the problem by adding "noapic" to the kernel line in menu.lst

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=60aa0ef0-121f-478e-a90c-c229d150e290 ro quiet splash noapic

(all on one line)

---

