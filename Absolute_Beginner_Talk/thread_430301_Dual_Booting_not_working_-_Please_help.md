---
title: "Dual Booting not working - Please help"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by Ameliorate on 2007-05-02
I just installed Ubuntu on my computer and I am not able to run windows any longer
I have windows on a 250GB HD and i installed Ubuntu to a secondary 160GB HD but i am no longer able to run windows. What do i need to do to be able to dual boot successfully?

---

### Post by truth_forum on 2007-05-02
same here. 

ive upgraded from dapper to edgy using alternate cd and after the upgrade when i booted, my xp was deleted as one of the choices for booting, all choices now are 6.06 and 6.10 (with generic and recovery modes) i have a dual boot with dapper.  

when booting there are also issues with RAID (failed) avahi???  (failed) 

and after the ubuntu splashscreen, which is very nice (6.10)  no picture will appear and it says that the xserver not configured (NVIDIA). 
already installed the nvidia drivers and Im trying to configure the xserver... but dont know about the RAID , avahi??? and how to restore the  XP...  

help please??? 

thanks

---

### Post by Billy McCann on 2007-05-02
Both of you need to paste the output of two commands for us.  

The first command that you need to type into the terminal is 

```
sudo fdisk -l
```

The second is 

```
cat /boot/grub/menu.lst
```


The output of these commands will give us an indication of how your partitions are set up and how your GRUB is configured.  Please type those commands into a terminal and then paste the output here.   

This will help me and anyone else who's willing to help get a better picture of just how things need to be tweaked.  

:KS

---

### Post by truth_forum on 2007-05-02
thanks. will try that when i get home... and post the output.. thanks

---

### Post by Ameliorate on 2007-05-02
> **Billy McCann said:**
> Both of you need to paste the output of two commands for us.  

The first command that you need to type into the terminal is 

```
sudo fdisk -l
```

The second is 

```
cat /boot/grub/menu.lst
```


The output of these commands will give us an indication of how your partitions are set up and how your GRUB is configured.  Please type those commands into a terminal and then paste the output here.   

This will help me and anyone else who's willing to help get a better picture of just how things need to be tweaked.  

:KS


first output

 sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


second output

cat /boot/grub/menu.lit
cat: /boot/grub/menu.lit: No such file or directory
kent@kent-desktop:~$ cat /boot/grub/menu.lst
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
timeout         3

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
# kopt=root=UUID=b044190d-1dbb-4c7a-a4a9-d7d8ef11c0b0 ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b044190d-1dbb-4c7a-a4a9-d7d8ef11c0b0 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=b044190d-1dbb-4c7a-a4a9-d7d8ef11c0b0 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Bartender on 2007-05-02
try 
```
sudo fdisk -l
```

it's fdisk with an "ell", not a "one"

---

### Post by Bartender on 2007-05-02
From the output of "menu.lst" it looks like you've overwritten Windows with Linux.  Or at the least GRUB doesn't know Windows is there.  That's why we'll need the output of fdisk -l.

The "menu.lst" query tells you what operating systems GRUB thinks are available.

fdisk -l tells you what partitions Linux sees.

---

### Post by confused57 on 2007-05-02
> **Ameliorate said:**
> I just installed Ubuntu on my computer and I am not able to run windows any longer
I have windows on a 250GB HD and i installed Ubuntu to a secondary 160GB HD but i am no longer able to run windows. What do i need to do to be able to dual boot successfully?

Maybe this guide will help:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

may be just a matter of adding a Window's entry to your menu.lst.

---

### Post by Ameliorate on 2007-05-02
this is the output of the correct command. However, i  think i have accidentally deleted windows



Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           1           0    0  Empty
Partition 1 does not end on cylinder boundary.

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        1459    11719386   83  Linux
/dev/hdd2            1460        1763     2441880   82  Linux swap / Solaris
/dev/hdd3            1764        3014    10048657+  83  Linux
/dev/hdd4            3015       19457   132078397+  83  Linux

---

### Post by Bartender on 2007-05-02
Sure looks like sda1 is empty, or at least it's unreadable by Linux.

It seems odd though that your second drive is listed as hdd.  I'd expect it to be hdb.  Not that that's very important compared to your bigger problem..

I'm not sure what "Partition 1 does not end on cylinder boundary" means.

Another thing to try...toss in a LiveCD and go to Gnome Partitioner.  I think it's under "System" > "Administration".  Bring up the partitioner and ask it to look at sda.  See if it shows the drive as blank or if it has data.  Maybe your MBR got corrupted and you can fix that.

---

### Post by truth_forum on 2007-05-02
this is the output of fdisk -l

disk/dev/hda: 40G
                    boot     start        end               blocks                id           system
dev/hda1     *          197          4864              37495710      7             HPFS/NTFS


disk/dev/hdb: 40G

dev/hdb1/    *         1             1912                15358108+    7       HPFS/NTFS
        hdb2              1913        2611                     5614717+  f       W95 Beta (LBA)
        hdb3              2612          4870              18145417+     83    linux
        hdb5              1913        2374                3710983+       82    linux 
        hdb6               2375        2511                1100421           82   linux/swap/solaris
         hdb7             2512         2611                 803218+     82      linux/swap/solaris


cat /boot/grub/menu.lst
cat: /: Ls is a directory
cat : boot/grub/menu.st: no such file or directory 


by the way was able to fix the xserver (sudo apt-get install xserver-xorg) and i am now using edgy to post this.. :) 

should hda1 start with 1 and not 197? 

have 2 HD 40G each.  

have i deleted my xp? 

thanks for the help....

---

### Post by truth_forum on 2007-05-02
sorry, forgot that i could copy the terminal. 
this is the entry in the terminal: 

fdisk -l 

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         197        4864    37495710    7  HPFS/NTFS

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hdb2            1913        2611     5614717+   f  W95 Ext'd (LBA)
/dev/hdb3            2612        4870    18145417+  83  Linux
/dev/hdb5            1913        2374     3710983+  83  Linux
/dev/hdb6            2375        2511     1100421   82  Linux swap / Solaris
/dev/hdb7            2512        2611      803218+  82  Linux swap / Solaris

:~$ cat / boot/grub/menu.lst
cat: /: Is a directory
cat: boot/grub/menu.lst: No such file or directory


/dev/hda1   *         197        4864    37495710    7  HPFS/NTFS 

should this start with 1?

thanks for the help...

---

### Post by Billy McCann on 2007-05-02
truthforum,

copy and paste this (exactly) into the terminal.

```
cat /boot/grub/menu.lst
```

And paste the output for us.  :)

From the looks of the output of fdisk -l, it would seem you still have you Windows partitions (hda1, hdb1).  We just need to make sure GRUB knows where to look for them.

---

### Post by truth_forum on 2007-05-02
thanks for the proper command, anyway here is the output. 
this seems complicated. i also want to delete the dappers and how can i restore the xp? many thanks..

:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

title           Ubuntu, kernel 2.6.17-10-386
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, kernel 2.6.15-28-386
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-28-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-27-386
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-27-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro single
initrd          /boot/initrd.img-2.6.15-27-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=UUID=fc45a698-9630-40ef-b719-06e6ad8a1c87 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Windows NT/2000/XP (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Billy McCann on 2007-05-02
Well, GRUB seems to be looking in the right spots for Windows and the entries definitely are there.  I'm not sure why you cannot select to boot from Windows, unless it has something to do with the RAID failure.  

Sorry I can't help any further.

---

### Post by Ameliorate on 2007-05-02
There is something on sda1
I used the live cd and got to the partitioner in the install and it said this about my 250 GB HD:
/dev/sda
   free space                 250059MB
/dev/sdb
   /dev/sdb1                  2048MB

Any chance I still have Windows?
[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by Ameliorate on 2007-05-02
There is something on sda1
I used the live cd and got to the partitioner in the install and it said this about my 250 GB HD:
/dev/sda
   free space                 250059MB
/dev/sdb
   /dev/sdb1                  2048MB

Any chance I still have Windows?
[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by Ameliorate on 2007-05-02
I booted to the live cd and it said
/dev/sda
    was empty except for
/dev/sda1
        has 2024 mb on it - is this the recovery partition for windows? if so how do i access it?

---

### Post by Billy McCann on 2007-05-03
> **Ameliorate said:**
> Any chance I still have Windows?
According to this 

/dev/sda
   free space                 250059MB

Windows is either not there are it is unreadable.  Sorry for the bad news.  :(

---

### Post by Billy McCann on 2007-05-03
> **Ameliorate said:**
> I booted to the live cd and it said
/dev/sda
    was empty except for
/dev/sda1
        has 2024 mb on it - is this the recovery partition for windows? if so how do i access it?
Try using a Super Grub Disc ([download](http://linux.softpedia.com/get/System/Boot/Super-Grub-Disk-8071.shtml)) to boot into the recovery partition.

---

### Post by truth_forum on 2007-05-05
thanks for all the help.. the xp is still there all the while :popcorn: sorry i just failed see and  move the cursor down and below the other operating systems when booting....i am embarrassed.. anyway for all the help given,, thank you very much and more power....

---

### Post by Billy McCann on 2007-05-05
:lolflag:

---

