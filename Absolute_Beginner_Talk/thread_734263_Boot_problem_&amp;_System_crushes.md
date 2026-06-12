---
title: "Boot problem &amp; System crushes"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by cannabis on 2008-03-24
Im able to boot my Linux only after several reboots becouse at the first boot bar moves a bit forward and then black screen coming up (From other topic: "I see the swerving orange rectangle, and then the load bar, and then, a black screen, with my lowly flashing underscore in the top left.").. after several restarts by pressing CTRL + ALT + DELETE system boots properly. Why so? Also it crushes sometimes just freezes and I have no choise I cant do anything exept pressing RESTART button :( 
I have tried to press CTRL + ALT + F1 when I got this black screen, So here is the screenshot of **error log**. I dont have Windows on the same HDD only Ubuntu. How these two pretty crusual problems can be solved?

[[IMG]http://img26.picoodle.com/img/img26/4/3/24/t_DSC00784m_39222f2.jpg[/IMG]](http://www.picoodle.com/view.php?img=/4/3/24/f_DSC00784m_39222f2.jpg&srv=img26)

Here is **etc/fstab**:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=d9acdb8c-9a12-4e0c-8105-3dd71ea20ece /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=d06e9228-0b32-438c-a1c1-b1a7a0e6af41 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Here is [B]sudo lspci | grep -i vga
grep -i driver /etc/X11/xorg.con[/B]:
> 
cannabis@cannabis-desktop:~$ sudo lspci | grep -i vga
[sudo] password for cannabis:
05:00.0 VGA compatible controller: ATI Technologies Inc RV410 [Radeon X700 Pro (PCIE)]
cannabis@cannabis-desktop:~$ grep -i driver /etc/X11/xorg.conf
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "ati"
cannabis@cannabis-desktop:~$ 


and here is **df -h**:

> cannabis@cannabis-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdd1              18G  7,4G  9,6G  44% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
cannabis@cannabis-desktop:~$ 


Here is **sudo fdisk -l**:

> cannabis@cannabis-desktop:~$ sudo fdisk -l
[sudo] password for cannabis:

Disk /dev/hdd: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeedceedc

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2372    19053058+  83  Linux
/dev/hdd2            2373        2480      867510    5  Extended
/dev/hdd5            2373        2480      867478+  82  Linux swap / Solaris
cannabis@cannabis-desktop:~$ 


**Thank you all!**

---

### Post by drascus on 2008-03-24
I had a similar error before. I resolved it by going to terminal type sudo gedit /boot/grub/menu.lst

at the bottom after end default settings there is a line that looks like this:
 kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=58ccc2dc-6dbc-4534-8948-c699eefd936c ro quiet splash

delete splash save the file and reboot see if that helps..

---

### Post by cannabis on 2008-03-24
> **drascus said:**
> I had a similar error before. I resolved it by going to terminal type sudo gedit /boot/grub/menu.lst

at the bottom after end default settings there is a line that looks like this:
 kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=58ccc2dc-6dbc-4534-8948-c699eefd936c ro quiet splash

delete splash save the file and reboot see if that helps..


Hmm .. not helped same problems. Just boot bar is gone but still can't boot properly? Any other ideas?

Thanx!

---

### Post by drascus on 2008-03-24
hmm not sure if its a laptop you might want to post this question in the laptop forums. Also you can always check the #ubuntu channel in IRC if you need more immediate assistance.  Anyone else have any ideas?

---

### Post by cannabis on 2008-03-25
> **drascus said:**
> hmm not sure if its a laptop you might want to post this question in the laptop forums. Also you can always check the #ubuntu channel in IRC if you need more immediate assistance.  Anyone else have any ideas?

Hi its not a laptop just a PC. With 
AMD Athlon 3000+
Ati Sapphire X700 Pro 256Mb
1024Mb Kingston DDR
and test with HDD 20 Gb

Thx, I think I should check IRC channel..

Here is some more helpful information..:

**/boot/grub/menu.lst**:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
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
# kopt=root=UUID=d9acdb8c-9a12-4e0c-8105-3dd71ea20ece ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d9acdb8c-9a12-4e0c-8105-3dd71ea20ece ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d9acdb8c-9a12-4e0c-8105-3dd71ea20ece ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

**/etc/fstab** after chengind UUID line to **/dev/hdd5 none swap sw 0 0**:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=d9acdb8c-9a12-4e0c-8105-3dd71ea20ece /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
/dev/hdd5 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

**free** command:

> cannabis@cannabis-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035636     620920     414716          0     108220     295072
-/+ buffers/cache:     217628     818008
Swap:       867468          0     867468
cannabis@cannabis-desktop:~$ 


---

### Post by cannabis on 2008-03-25
Any ideas boys? Pretty bad thing that I have to reboot it after 1-2 hours. Always afraid if it freezes now.. :(

---

