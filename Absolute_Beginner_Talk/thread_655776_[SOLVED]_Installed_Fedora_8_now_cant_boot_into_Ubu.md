---
title: "[SOLVED] Installed Fedora 8 now cant boot into Ubuntu anymore"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2008-01-01
How do I get it so grub loads and I can choose both Ubuntu and Fedora? Very noob at this so detailed instructions would help greatly!

---

### Post by jken146 on 2008-01-01
Hi there.  Please post the outputs of these 2 commands:
```
sudo fdisk -l
```
```
cat /boot/grub/menu.lst
```

---

### Post by xeth_delta on 2008-01-01
Let me see if I understand correctly. You installed Fedora on a different partition and now grub (the boot loader) does not show the option to boot ubuntu, right? The MBR and hence grub was most likely over written, in that case. It would be a matter of adding the respective ubuntu lines to the grub configuration file currently in used, the one made by Fedora.

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> Let me see if I understand correctly. You installed Fedora on a different partition and now grub (the boot loader) does not show the option to boot ubuntu, right? The MBR and hence grub was most likely over written, in that case. It would be a matter of adding the respective ubuntu lines to the grub configuration file currently in used, the one made by Fedora.

How would I do this?  Do I need to navigate to it in the terminal?  If so how what commands do I type?  Also the fdisk and other commands that were posted earlier dont seem to work for me in Fedora.  Right now I am in fedora since I cant figure out how to get into Ubuntu.

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> How would I do this?  Do I need to navigate to it in the terminal?  If so how what commands do I type?  Also the fdisk and other commands that were posted earlier dont seem to work for me in Fedora.  Right now I am in fedora since I cant figure out how to get into Ubuntu.

Did you try with sudo? I think you should have the root user available by default in Fedora. Try becoming root in a terminal with "su". Then try again those commands I told you, they will help you identify which one is your ubuntu partition. Do you perchance already know which one it is? You will need to mount it and indeed do some work in the terminal.

Thinking of it, maybe it was already mounted. What is the output of:

```
sudo mount
```
or as root
```
mount
```

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> Did you try with sudo? I think you should have the root user available by default in Fedora. Try becoming root in a terminal with "su". Then try again those commands I told you, they will help you identify which one is your ubuntu partition. Do you perchance already know which one it is? You will need to mount it and indeed do some work in the terminal.

Thinking of it, maybe it was already mounted. What is the output of:

```
sudo mount
```
or as root
```
mount
```

here is my output after typing mount in the root terminal 

/dev/sda4 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> here is my output after typing mount in the root terminal 

/dev/sda4 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)

It is not mounted, you will have to do it. Try the commands I mentioned, as root. Post the output here.

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> It is not mounted, you will have to do it. Try the commands I mentioned, as root. Post the output here.

I feel stupid for asking this but which commands that you mentioned do you mean? :)

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> I feel stupid for asking this but which commands that you mentioned do you mean? :)

Now I feel a bit awkward :p I was replying to another thread that required those commands, too, and thought I posted them here too. Sorry for the confusion.

Here there are:
As root:
```
fdisk -l
```

Be **very** careful with the following command, as you could potentially damage your partition table if you do something wrong and save the changes. We'll assume your harddisk is sda:
```
sudo parted /dev/sda
```
You will be presented with a parted prompt:
```
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
```
Press "p" followed by ENTER. A list with the partitions of the hard disk will be shown. Please post them here. Quit pressing "q" followed by ENTER.

Xeth

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> Now I feel a bit awkward :p I was replying to another thread that required those commands, too, and thought I posted them here too. Sorry for the confusion.

Here there are:
As root:
```
fdisk -l
```

Be **very** careful with the following command, as you could potentially damage your partition table if you do something wrong and save the changes. We'll assume your harddisk is sda:
```
sudo parted /dev/sda
```
You will be presented with a parted prompt:
```
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
```
Press "p" followed by ENTER. A list with the partitions of the hard disk will be shown. Please post them here. Quit pressing "q" followed by ENTER.

Xeth

Ok, I think weve got a problem now.  I typed both the first two commands in root terminal and it tells me that the commands are not found. :confused:

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> Ok, I think weve got a problem now.  I typed both the first two commands in root terminal and it tells me that the commands are not found. :confused:

Try sfdisk instead of fdisk. If that does not work, /sbin/sfdisk or /sbin/fdisk.
There is a possibility (though I doubt it would be the case) these programs are not installed. I am not familiar with the package management system of Fedora, but I think it is called yum.

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> Try sfdisk instead of fdisk. If that does not work, /sbin/sfdisk or /sbin/fdisk.
There is a possibility (though I doubt it would be the case) these programs are not installed. I am not familiar with the package management system of Fedora, but I think it is called yum.

Ok, one of the commands worked for fdisk :) Here is the output for that. 

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       12226    77722470   83  Linux
/dev/sda3           14351       14410      481950    5  Extended
/dev/sda4           12227       14350    17061030   83  Linux
/dev/sda5           14351       14410      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

I think Ubuntu is located on /dev/sda2 because I remember making 77 gb of space for it.

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> Ok, one of the commands worked for fdisk :) Here is the output for that. 

Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       12226    77722470   83  Linux
/dev/sda3           14351       14410      481950    5  Extended
/dev/sda4           12227       14350    17061030   83  Linux
/dev/sda5           14351       14410      481918+  82  Linux swap / Solaris

Partition table entries are not in disk order

I think Ubuntu is located on /dev/sda2 because I remember making 77 gb of space for it.

Good, in that case you will need to mount that partition. Start by creating a new directory in mnt to mount your Ubuntu partition. The following two commands are to be run as root in Fedora:

```
mkdir /mnt/ubuntu
mount /dev/sda2 /mnt/ubuntu
```

Open the following files and post the output here:
The Ubuntu one:
```
/mnt/ubuntu/boot/grub/menu.lst
```
and the one from Fedora:
```
/boot/grub/grub.conf
```
if I recall right from my RedHat days.

---

### Post by hockeyfighter09 on 2008-01-01
Ok, the mkdir and mount commands worked without problem, but when I try to mount the Ubuntu partition that is in the 2nd code box you gave me it tells me permission denied.

---

### Post by kevdog on 2008-01-01
Preface the mount command with sudo

---

### Post by hockeyfighter09 on 2008-01-01
> **kevdog said:**
> Preface the mount command with sudo

I tried that too and it tells me command not found.

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> I tried that too and it tells me command not found.

Silly question. Did you run mount as root?

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> Silly question. Did you run mount as root?

Yea, I opened terminal then typed in su then the first two commands went smoothly then I ran into issues.

---

### Post by jken146 on 2008-01-01
> **hockeyfighter09 said:**
> Ok, the mkdir and mount commands worked without problem, but when I try to mount the Ubuntu partition that is in the 2nd code box you gave me it tells me permission denied.

There is no mount command in the second code box.  You were asked to post the contents of those files, i.e. ```
cat /mnt/ubuntu/boot/grub/menu.lst
``` and ```
cat /boot/grub/menu.lst
```

---

### Post by hockeyfighter09 on 2008-01-01
> **jken146 said:**
> There is no mount command in the second code box.  You were asked to post the contents of those files, i.e. ```
cat /mnt/ubuntu/boot/grub/menu.lst
``` and ```
cat /boot/grub/menu.lst
```

here is the output of the first code,


[HTML]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Media Center Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1



[/HTML]


Heres the output for the 2nd code

[HTML][root@localhost aaron]# cat /boot/grub/menu.lst
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,3)
#          kernel /boot/vmlinuz-version ro root=/dev/sda4
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,3)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.9-85.fc8)
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.23.9-85.fc8 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.23.9-85.fc8.img
title Fedora (2.6.23.1-42.fc8)
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.23.1-42.fc8.img
title Other
        rootnoverify (hd0,0)
        chainloader +1
[/HTML]

---

### Post by jken146 on 2008-01-01
Right, so you need to copy the entries for Ubuntu from Ubuntu's menu.lst file and add them to Fedora's grub.conf file.

```
nano /boot/grub/grub.conf
```

And paste the following at the end:
```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

```

Then press Ctrl+X then Y then enter to save and exit.

---

### Post by hockeyfighter09 on 2008-01-01
Can I log into Ubuntu now that I did that?

---

### Post by jken146 on 2008-01-01
I should hope so.  Reboot and try it!

---

### Post by xeth_delta on 2008-01-01
Ok, we are getting closer to solve this.

1: Tking care of /boot/grub/grub.conf
Start by making a backup of **/boot/grub/grub.conf** or **/boot/grub/menu.lst** so that you can restore it from a live CD in case of disaster.

If you have a look at your /mnt/ubuntu/boot/grub.conf, the lines we are interested in are:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

So, what you will have to do is add them to the end of **/boot/grub/grub.conf**, as root. Your file should look like:

```
# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,3)
#          kernel /boot/vmlinuz-version ro root=/dev/sda4
#          initrd /boot/initrd-version.img
#boot=/dev/sda
default=0
timeout=5
splashimage=(hd0,3)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.9-85.fc8)
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.23.9-85.fc8 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.23.9-85.fc8.img
title Fedora (2.6.23.1-42.fc8)
        root (hd0,3)
        kernel /boot/vmlinuz-2.6.23.1-42.fc8 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd-2.6.23.1-42.fc8.img
title Other
        rootnoverify (hd0,0)
        chainloader +1

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

2: [EDIT] As observed by jken146, the step described here was not necessary. For reference, it involved copying some files to /boot/

After this, I think you should be ready to go. Please check the new configuration file for any mistake, and please let us know how it went. I have one more comment about your swap partition I will write on the next post.

Good luck!
Xeth

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> Can I log into Ubuntu now that I did that?

[EDIT] post changed. As jken146 observed, the copy of certain files to the Fedora /boot/ was not necessary.

---

### Post by jken146 on 2008-01-01
> **xeth_delta said:**
> jken146 is right, but I am afraid you will also need to copy the kernel image and associated files to the Fedora /boot/

Why must he copy the Ubuntu kernel image etc. to the Fedora /boot directory?  I was under the impression that GRUB looks for the kernel image in the path specified with "kernel", taking / to be whatever is specified with "root".  I am dual booting Xubuntu and Arch right now and have not had to move around any kernel images.

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> jken146 is right, but I am afraid you will also need to copy the kernel image and associated files to the Fedora /boot/

Will this work by just copying the second code you gave me in your last post?

---

### Post by xeth_delta on 2008-01-01
About your swap partition. I noticed you re using the same swap for ubuntu and Fedora. I don't think there would generally be any problem with that (For this you might be interested in asking in the forum, as I have not tried to have a shared swap), except for hibernation.

I kindly ask to be corrected if I am wrong. During hibernation the contents of the data located in RAM is saved in the swap partition, to be recovered during resume.Under certain (rare) circumstances there can be data corruption, if more than one kernel have access to the same swap.

Let me give you an example.
-Hibernation in Ubuntu (RAM data now saved in swap)
-Boot Fedora (over-writes swap with own data)
-Quit Fedora
-Boot again Ubuntu, it was in hiberbation, resumes, hence looks for data in swap to be placed back in RAM. Wrong data now in RAM. Potential data corruption!

The same would be if you have more than one kernel to boot from in Ubuntu.
I did not want to scare you, just to make you aware that you have to be careful with hibernation and multiple kernels. As long as you don't make a mistake as the one I descrived above, you should be OK.

Xeth

---

### Post by hockeyfighter09 on 2008-01-01
When I open my /mnt/ubuntu/boot/ theres nothing in it.  So i cant transfer anything to /boot/

---

### Post by xeth_delta on 2008-01-01
> **jken146 said:**
> Why must he copy the Ubuntu kernel image etc. to the Fedora /boot directory?  I was under the impression that GRUB looks for the kernel image in the path specified with "kernel", taking / to be whatever is specified with "root".  I am dual booting Xubuntu and Arch right now and have not had to move around any kernel images.

Hmmm, You might be right after all. I think I got a little confused about that. I stand corrected.

hockeyfighter09, did you manage to boot Ubunu after just adding the lines to grub.conf?

---

### Post by hockeyfighter09 on 2008-01-01
> **xeth_delta said:**
> About your swap partition. I noticed you re using the same swap for ubuntu and Fedora. I don't think there would generally be any problem with that (For this you might be interested in asking in the forum, as I have not tried to have a shared swap), except for hibernation.

I kindly ask to be corrected if I am wrong. During hibernation the contents of the data located in RAM is saved in the swap partition, to be recovered during resume.Under certain (rare) circumstances there can be data corruption, if more than one kernel have access to the same swap.

Let me give you an example.
-Hibernation in Ubuntu (RAM data now saved in swap)
-Boot Fedora (over-writes swap with own data)
-Quit Fedora
-Boot again Ubuntu, it was in hiberbation, resumes, hence looks for data in swap to be placed back in RAM. Wrong data now in RAM. Potential data corruption!

The same would be if you have more than one kernel to boot from in Ubuntu.
I did not want to scare you, just to make you aware that you have to be careful with hibernation and multiple kernels. As long as you don't make a mistake as the one I descrived above, you should be OK.

Xeth

I dont think I would be affected by this because I rarely if ever use hibernate, I usually just use standby.

---

### Post by jken146 on 2008-01-01
Could you boot into Ubuntu after adding those entries to /boot/grub.conf?

---

### Post by hockeyfighter09 on 2008-01-01
> **jken146 said:**
> Could you boot into Ubuntu after adding those entries to /boot/grub.conf?

Nope, Ubuntu was still not an option.  I am going to try again though right now.

---

### Post by jken146 on 2008-01-01
Weird.  Are you pressing Escape to get to the GRUB menu?

Please post the contents of your grub.conf file again, that is,
```
cat /boot/grub/grub.conf
```

---

### Post by hockeyfighter09 on 2008-01-01
> **jken146 said:**
> Weird.  Are you pressing Escape to get to the GRUB menu?

Please post the contents of your grub.conf file again, that is,
```
cat /boot/grub/grub.conf
```

I rebooted again and now ubuntu is an option on the menu.  However I get an error message saying a bunch of stuff then "Error 11: Unrecognized device string"  I am thinking that the thing holding me back is the kernel image xeth_delta was saying about earlier.

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> I rebooted again and now ubuntu is an option on the menu.  However I get an error message saying a bunch of stuff then "Error 11: Unrecognized device string"  I am thinking that the thing holding me back is the kernel image xeth_delta was saying about earlier.

Could it be the device UUID used in Ubuntu?

---

### Post by xeth_delta on 2008-01-01
Make a back-up of grub.conf and then try changing in /boot/grub/grub.conf

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

To

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

---

### Post by jken146 on 2008-01-01
> **xeth_delta said:**
> Could it be the device UUID used in Ubuntu?

I guess it could well be.

---

### Post by hockeyfighter09 on 2008-01-01
[HTML]Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'

root          (hd0,1) 
  Filesystem type is ext2fs, partition type 0x83
kernel                /boot/vmlinuz-2.6.22-14-generic
  [Linux-bzImage,  setup=0x1e00,  size=0x1acc58]
roo=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash

Error 11: Unrecognized device string

Press any key to continue[/HTML]


That is the message I get when choosing ubuntu from the boot menu list

---

### Post by xeth_delta on 2008-01-01
> **hockeyfighter09 said:**
> [HTML]Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'

root          (hd0,1) 
  Filesystem type is ext2fs, partition type 0x83
kernel                /boot/vmlinuz-2.6.22-14-generic
  [Linux-bzImage,  setup=0x1e00,  size=0x1acc58]
roo=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash

Error 11: Unrecognized device string

Press any key to continue[/HTML]


That is the message I get when choosing ubuntu from the boot menu list

From that I deduce it is the UUID string.

---

### Post by jken146 on 2008-01-01
> **xeth_delta said:**
> Make a back-up of grub.conf and then try changing in /boot/grub/grub.conf

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

To

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

That sounds good.  If that doesn't work though. change the root line in the "Other" option to ```
root    (hd0,1)
``` so that the Fedora bootloader passes you on to the Ubuntu bootloader.

---

### Post by jken146 on 2008-01-01
STOP!!
The problem is in **bold**:
> **hockeyfighter09 said:**
> ```
Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'

root          (hd0,1) 
  Filesystem type is ext2fs, partition type 0x83
kernel                /boot/vmlinuz-2.6.22-14-generic
  [Linux-bzImage,  setup=0x1e00,  size=0x1acc58]
**roo=UUID=a168871b-6d78-41bb-a727-7d964fd8ed2d ro quiet splash**

Error 11: Unrecognized device string

Press any key to continue
```


That is the message I get when choosing ubuntu from the boot menu list

It should say **root**=UUID=....... not **roo**=UUID=.......

---

### Post by hockeyfighter09 on 2008-01-01
> **jken146 said:**
> STOP!!
The problem is in **bold**:


It should say **root**=UUID=....... not **roo**=UUID=.......

Im restarting to check.  I typed that all by hand so it might be an error on my part.

---

### Post by xeth_delta on 2008-01-01
> **jken146 said:**
> STOP!!
The problem is in **bold**:


It should say **root**=UUID=....... not **roo**=UUID=.......

Ha! Typo, well spotted jken146!

---

### Post by hockeyfighter09 on 2008-01-01
Its an error by me.  It does say root so that isnt the problem probably.

---

### Post by jken146 on 2008-01-02
OK, I see.  Did you try Xeth_Delta's suggestion of removing the UUID bits?

---

### Post by hockeyfighter09 on 2008-01-02
Changed the things around in the /boot/grub/grub.conf as mentioned above.  Restarted and now it gets to the screen where it says Ubuntu and the orange loading bar.  Now the bar is stuck and not moving.

---

### Post by jken146 on 2008-01-02
Success!  Well, at least GRUB is fixed.  Now we need to get some more info as to why Ubuntu is misbehaving.

Did you move the kernel image as was mentioned above (I don't think you needed to do this)?  I doubt that that would be the problem anyway.

When you're at the GRUB menu, go to the Ubuntu line and press **e**.  Then edit the kernel line to remove the work **quiet**.  Post any error messages you see.

---

### Post by hockeyfighter09 on 2008-01-02
> **jken146 said:**
> Success!  Well, at least GRUB is fixed.  Now we need to get some more info as to why Ubuntu is misbehaving.

Did you move the kernel image as was mentioned above (I don't think you needed to do this)?

Xeth_delta said to transfer the image from the /mnt/ubuntu/boot/ to /boot/ but the problem is when I ope the /mnt/ubuntu/boot/ in terminal there is nothing there to transfer to /boot/

---

### Post by xeth_delta on 2008-01-02
> **hockeyfighter09 said:**
> Xeth_delta said to transfer the image from the /mnt/ubuntu/boot/ to /boot/ but the problem is when I ope the /mnt/ubuntu/boot/ in terminal there is nothing there to transfer to /boot/

Be careful, do not remove the image from your Ubuntu /boot. What I meant earlier was to make a copy to place in the Fedora /boot, but I am afraid that was not necessary at all. Otherwise the kernel would not have been found when booting.

---

### Post by hockeyfighter09 on 2008-01-02
> **xeth_delta said:**
> Be careful, do not remove the image from your Ubuntu /boot. What I meant earlier was to make a copy to place in the Fedora /boot, but I am afraid that was not necessary at all. Otherwise the kernel would not have been found when booting.

So then this step is not required to make Ubuntu work again?

---

### Post by jken146 on 2008-01-02
> **hockeyfighter09 said:**
> Xeth_delta said to transfer the image from the /mnt/ubuntu/boot/ to /boot/ but the problem is when I ope the /mnt/ubuntu/boot/ in terminal there is nothing there to transfer to /boot/

OK, that's probably because sda2 isn't mounted.  ```
mount /dev/sda2 /mnt/ubuntu
```
I'm not sure you should transfer the file though, as /boot on the Fedora partition isn't where GRUB looks for the Ubuntu kernel image.  Anyway, the image has been found so Ubuntu is booting from it.  In short: forget about this for now.

Try Recovery Mode and tell us what it says when it hangs.

---

### Post by xeth_delta on 2008-01-02
> **hockeyfighter09 said:**
> So then this step is not required to make Ubuntu work again?

As far as I can see, it is not. Did you try jken146's suggestion? Commenting out the "quiet splash" part and then posting the seen errors.

---

### Post by hockeyfighter09 on 2008-01-02
Ok i rebooted into recovery mode and it lists huge amount of information that is way to long to type out it looks like its showing the hardware in my computer.  Then at a certain point it just stops and sits there doing nothing.

---

### Post by jken146 on 2008-01-02
What's the last thing it says when it stops?

---

### Post by hockeyfighter09 on 2008-01-02
> **jken146 said:**
> What's the last thing it says when it stops?

Right now i just tried your suggestion of removing quiet splash and it loads like it did in recovery mode then stops at. 

/build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

Thats the last things on the list.

---

### Post by iansane on 2008-01-02
I'm a newb myself so sorry if this doesn't pertain to the situation but I've installed a few different dual boot systems (all with windows as the first os)  and when windows has to be reinstalled and it rewrites the boot loader like that I just reinstall grub  from the live cd.
It reads all the partitions and drives and rewrites grub.
heres where I learned how.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once agian, sorry if it doesn't partain to this situation

---

### Post by hockeyfighter09 on 2008-01-02
It now moved and is telling me loads of things that have no such file or directory.  Things such as /root/sys
/root/proc
/sbin/init


then at the bottom it says (initramfs)
waiting for me to give it a command

---

### Post by xeth_delta on 2008-01-02
From a previous post, add the following line at the end of /boot/grub/grub.conf:
```
title Ubuntu Boot Loader
        rootnoverify (hd0,1)
        chainloader +1
```

And boot from it.

---

### Post by hockeyfighter09 on 2008-01-02
> **iansane said:**
> I'm a newb myself so sorry if this doesn't pertain to the situation but I've installed a few different dual boot systems (all with windows as the first os)  and when windows has to be reinstalled and it rewrites the boot loader like that I just reinstall grub  from the live cd.
It reads all the partitions and drives and rewrites grub.
heres where I learned how.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once agian, sorry if it doesn't partain to this situation

Sounds like it does!  Thanks for this suggestion I am gonna give this solution a try.

---

### Post by jken146 on 2008-01-02
> **iansane said:**
> I'm a newb myself so sorry if this doesn't pertain to the situation but I've installed a few different dual boot systems (all with windows as the first os)  and when windows has to be reinstalled and it rewrites the boot loader like that I just reinstall grub  from the live cd.
It reads all the partitions and drives and rewrites grub.
heres where I learned how.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once agian, sorry if it doesn't partain to this situation

Thanks for making a suggestion, iansane.  We've got GRUB to work though.  Ubuntu is starting,  but not getting all the way there.  I have to admit I don't know what to do next.  Hopefully someone will come along who knows more than I do (it shouldn't be too long, lol).  Best of luck, hockeyfighter.

---

### Post by hockeyfighter09 on 2008-01-02
> **xeth_delta said:**
> From a previous post, add the following line at the end of /boot/grub/grub.conf:
```
title Ubuntu Boot Loader
        rootnoverify (hd0,1)
        chainloader +1
```

And boot from it.

Ill try this

---

### Post by xeth_delta on 2008-01-02
> **iansane said:**
> I'm a newb myself so sorry if this doesn't pertain to the situation but I've installed a few different dual boot systems (all with windows as the first os)  and when windows has to be reinstalled and it rewrites the boot loader like that I just reinstall grub  from the live cd.
It reads all the partitions and drives and rewrites grub.
heres where I learned how.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Once agian, sorry if it doesn't partain to this situation

iansane, no need to apologize, you might be up to something.
Something similar to what you are describing happened here, only in this case it was another Linux distro who overwrote the MBR.
The method you mentioned could very well be used. The thing is, if the OP wants to be able to boot Ubuntu and Fedora he will have to slightly modify one of the boot loaders config files to accomodate both Linuxes. Thanks for a good suggestion, nevertheless!

---

### Post by hockeyfighter09 on 2008-01-02
> **xeth_delta said:**
> From a previous post, add the following line at the end of /boot/grub/grub.conf:
```
title Ubuntu Boot Loader
        rootnoverify (hd0,1)
        chainloader +1
```

And boot from it.

Does this require me to remove the "quiet splash" from the boot line of the kernel of Ubuntu in the boot menu?

---

### Post by xeth_delta on 2008-01-02
> **hockeyfighter09 said:**
> Does this require me to remove the "quiet splash" from the boot line of the kernel of Ubuntu in the boot menu?

Not really. Earlier you removed the "quiet splash" just to be able to read the messages.

---

### Post by hockeyfighter09 on 2008-01-02
Ok, Ubuntu Boot Loader showed up on the boot menu list and i get this when I choose it 


 Booting "Ubuntu Boot Loader'

rootnoverify       (hd0,1)
chainloader  +1

Error 13:  Invalid or unsupported executable format

Press any key to continue....

---

### Post by xeth_delta on 2008-01-02
> **hockeyfighter09 said:**
> Ok, Ubuntu Boot Loader showed up on the boot menu list and i get this when I choose it 


 Booting "Ubuntu Boot Loader'

rootnoverify       (hd0,1)
chainloader  +1

Error 13:  Invalid or unsupported executable format

Press any key to continue....

As I suspected... There's no boot loader in that partition. It was worth trying nevertheless. Remove the last block I suggested.
If you have time and patience we can try something else that will most likely make it work.

---

### Post by hockeyfighter09 on 2008-01-02
> **xeth_delta said:**
> As I suspected... There's no boot loader in that partition. It was worth trying nevertheless. Remove the last block I suggested.
If you have time and patience we can try something else that will most likely make it work.

Im up for another way if you are.  Or we can just continue another time and communicate through private messages.  Im in no hurry whatever works for you.

---

### Post by xeth_delta on 2008-01-02
I got another idea. In the lines:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

change **root=/** to **root=/dev/sda2**
Reboot and tell me how it went.

---

### Post by hockeyfighter09 on 2008-01-02
> **xeth_delta said:**
> I got another idea. In the lines:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=/ ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
```

change **root=/** to **root=/dev/sda2**
Reboot and tell me how it went.


IT WORKS!!! Thank you so much xeth_delta and also another big thanks to jken146 you guys are the reason I LOVE this community so much!  THANKS!:guitar:

---

### Post by xeth_delta on 2008-01-02
> **hockeyfighter09 said:**
> IT WORKS!!! Thank you so much xeth_delta and also another big thanks to jken146 you guys are the reason I LOVE this community so much!  THANKS!:guitar:

Fantastic!!!! You are welcome! I just remembered some of the options passed to the custom compiled kernels when I used RedHat 9 some years ago.

Good luck! Remember to mark the thread as solved.
Xeth

---

