---
title: "grub: error 25"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by zolw on 2007-05-10
I have problem. i encoutered problem: error disc read. The only way to start up Ubuntu is to use recovery mode (i have XP and Ubuntu on separated hd's - XP hda and U on hdb) No problems with boot till today :/.

- fsck under recovery mode shows no errors.
- when i try unplug one of disc or cdrom = error 17 - to get rid with dis one i had to reset BIOS
- when I run Gpatred via Live CD - both discs are visable, but hdab (ubuntu) have locks symbols... no idea what it mean
- XP is not booting too - same error 25
- i had tried to reinstall grub using apt-get install grub2 - all ok, no change in problem (nothig changed to be honest)

I have no idea wgat to do next. I could use Ubuntu in recovery mode any pressing control-d to load but its not very comfortable. any ideas whats gone wrong upon one night wen comp was turned off? :)

---

### Post by Najand on 2007-05-10
Give us the output of "sudo fdisk- l" on the live CD.

---

### Post by zolw on 2007-05-10
sudo fdisk -l

```
Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/hda2            6375       30400   192988845    f  W95 Ext'd (LBA)
/dev/hda5            6375       18485    97281576    7  HPFS/NTFS
/dev/hda6           18486       30400    95707206    7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3972    31905058+  83  Linux
/dev/hdb2            3973        9729    46243102+   f  W95 Ext'd (LBA)
/dev/hdb5            3973        8836    39070048+   7  HPFS/NTFS
/dev/hdb6            8837        9632     6393838+  83  Linux
/dev/hdb7            9633        9729      779121   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

ive encountered new error when fsck in recovery mode:

```

buffer I/O error on device hdb1 logical block [numbers here]

Ignore error? y (only option)
force rewrite? y (only option)

```

its impossible that my discs were physically damaged over night...

---

### Post by Najand on 2007-05-10
As far as you are able to do fdisk then it might be a way:
Open a terminal in the live CD:

```
mkdir /mnt/root
```

Then mount your partition in it. If you don't know which one it is, then mount any of them, we'll se if it's the correct one.

```
mount -t ext3 /dev/hdb1 /mnt/root
```

You can check if it's the correct one by running ls /mnt/root, which should output something like this :

> 
bin    dev      home        lib    mnt   root     srv  usr 
boot   etc      initrd      lib64  opt   sbin     sys  var
cdrom  initrd.img  media  proc  selinux  tmp  vmlinuz

Now that everything is mounted, we just need to reinstall GRUB :

```
grub-install --root-directory=/mnt/root /dev/hda
```

If all went well, you should see something like this :

> Installation finished. No error reported. 
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda

Now you can reboot and the GRUB menu should appear. If you see a warning message regarding XFS filesystem, you can ignore it.

---

### Post by zolw on 2007-05-10
I made this before, found solution on this board. Now i made it again with your instructions and get Error 15. I think you misunderstood me - i was getting error 25 after i choosed system (any except recovery mode or memtest). So grub was loadnig. till now. I bet i reboot now or make BIOS defaults and error 15 dissapear but error 25 after choosing system will be still prestent. any other ideas?

btw - i appreciate your help. ubuntuforums.org is the best support ever. much better than polish community - there i would get banned and ask to search in google. :)

---

### Post by Najand on 2007-05-10
Can you mount the Root (/) partition again and post your /boot/grub/menu.lst and /etc/fstab files here?

---

### Post by zolw on 2007-05-10
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default     0

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
# kopt=root=UUID=3ceeff73-14a8-47d1-9736-1b10e868ef92 ro

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3ceeff73-14a8-47d1-9736-1b10e868ef92 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3ceeff73-14a8-47d1-9736-1b10e868ef92 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=3ceeff73-14a8-47d1-9736-1b10e868ef92 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=069C204D9C203997 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=CCB01562B01553F4 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=8AE01D65E01D58B1 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=B264E35564E31B3D /media/hdb5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb6
UUID=0774002b-c5e6-428a-a4ae-6aad8c132606 /media/hdb6     ext3    defaults        0       2
# /dev/hdb7
UUID=e7c6ade1-8fd8-4254-89cd-f3e49fe1856e none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

