---
title: "drive space"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by johnmax on 2007-04-27
When I set up Ubuntu I allocated 75Gb but I have been merrily adding to the system and found this afternoon that I only have 3.5Gb.
When I look at the file directory I see 
/dev/hdb3 3.5Gb 
plus a number of smaller directories. 

What happened to the rest of the drive & how do I get it back?

---

### Post by Najand on 2007-04-27
Copy and paste the output of [CODE}sudo fdisk -l [/CODE] here.

---

### Post by johnmax on 2007-04-27
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb3             3.5G  3.2G   78M  98% /
varrun                443M   80K  442M   1% /var/run
varlock               443M     0  443M   0% /var/lock
procbususb             10M  136K  9.9M   2% /proc/bus/usb
udev                   10M  136K  9.9M   2% /dev
devshm                443M     0  443M   0% /dev/shm
lrm                   443M   18M  425M   4% /lib/modules/2.6.17-11-generic/volatile

---

### Post by Najand on 2007-04-27
What are your /dev/hda1 and /dev/hda2?

---

### Post by johnmax on 2007-04-28
Sorry,
hda1 and hda2 are where windows and a separate partition live on a separate drive. I split in two a separate 160G hard drive for Unbutu and any future OS.

John

---

### Post by Najand on 2007-04-28
Try to use gparted on the live cd or install it with apt-get/synaptic and check out your harddisk partition layout.

---

### Post by johnmax on 2007-04-28
Installed gparted with the following results;
/dev/hdb1  ext3  not mounted 72.49G
/dev/hdb3 ext3 /,/dev/static       3.5G
/dev/hdb4 extended                 188.26M
/dev/hdb5 linux-swap               188.23M

hdb1 had the following message with  triangle sign
"Unable to read this file system! Because of this some file operations may be unavailable. Did you install the correct plugin for this file system?

The drive was originally formated ntfs.

John

---

### Post by Najand on 2007-04-28
I see... Windows is on /dev/hda1? If you have just installed ubuntu then I recommend you to repartition and install it again.

---

### Post by johnmax on 2007-04-28
Windows is on hdba1 which is an SATA drive
hdb1, 2,3 ,4 ,5 all reside on a separate ATA drive. I have installed Ubuntu several times with  numerous updates and really hate to start over.

If I have to would I format the drive from windows or linux before I start again?

---

### Post by Najand on 2007-04-28
You don't need to format windows. Just Ubuntu.

---

### Post by johnmax on 2007-04-28
I really hate to start over but if I do should I reformat the entire drive from the CD? 

John

---

### Post by johnmax on 2007-04-28
The other more basic question is what happened when I installed Ubuntu to get me in this position?

---

### Post by Najand on 2007-04-28
Well... let us see... I don't gurantee anything, but I will help you to just copy your current Ubuntu to the 72GB space. First give me some information; like the output of the following commands:
1. cat /etc/fstab
2. cat /boot/grub/menu.lst

---

### Post by johnmax on 2007-04-28
the first command
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=04bba1ba-3cec-45aa-8e8d-cd61d6bda1dd none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by johnmax on 2007-04-28
the second
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
# kopt=root=UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows Vista/Longhorn (loader)
root            (hd1,3)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by Najand on 2007-04-28
If you are sure you don't have anything on /dev/hdb1, 
Use GPARTED and delete the partition and format it again as ext3. 
Then USING GPARTED AGAIN copy partition hdb3 to hdb1. DON'T DELETE PARTITION hdb3.
When you are done, let us continue.

---

### Post by johnmax on 2007-04-28
I am unable to copy hdb3 to hdb1 but the first two operations were completed. How do I copy it from one to the other?

---

### Post by Najand on 2007-04-28
Hmm, you are using the live CD or you have just installed GPARTED? If you are not using the live CD, use it. ANd try to umount partitions before copying them.

---

### Post by johnmax on 2007-04-28
Will do.
I will monitor the forum from another computer and report what happens.

---

### Post by Najand on 2007-04-28
Be careful not to delete the /dev/hdb3... That is very important.

---

### Post by johnmax on 2007-04-28
It is complete from thew CD. What do we do now?

---

### Post by Najand on 2007-04-28
Did you finish copying the /dev/hdb3 to /dev/hdb1?

---

### Post by johnmax on 2007-04-28
yes

---

### Post by Najand on 2007-04-28
OK, Can you mount /dev/hda1 and run:
sudo gedit /etc/fstab
in the terminal?

---

### Post by johnmax on 2007-04-28
let me restart and get out of the CD

---

### Post by Najand on 2007-04-28
You don't need to restart and remove CD... Let us continue in the LIVE CD mode.

---

### Post by johnmax on 2007-04-28
drat, let me restart in CD mode

---

### Post by Najand on 2007-04-28
OK.... When you restarted your computer, open a terminal and mount /dev/hda1:
```
$ sudo mount -t /dev/hda1 /mnt
```
and then 
```
$ sudo gedit /mnt/etc/fstab
```

---

### Post by Najand on 2007-04-28
Change it to something like (add blue parts):
```

the first command
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hdb3
[COLOR="Blue"]#[/COLOR]UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c / ext3 defaults,errors=remount-ro 0 1
[COLOR="Blue"]/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1[/COLOR]
# /dev/hdb5
[COLOR="Blue"]#[/COLOR]UUID=04bba1ba-3cec-45aa-8e8d-cd61d6bda1dd none swap sw 0 0
[COLOR="Blue"]/dev/hdb5 none swap sw 0 0[/COLOR]
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0

```

---

### Post by Najand on 2007-04-28
Then save and run;
```

$ sudo gedit /mnt/boot/grub/menu.lst

```

---

### Post by Najand on 2007-04-28
Try to chage all [COLOR="Red"]/dev/hdb3[/COLOR] to [COLOR="Blue"]/dev/hdb1[/COLOR]:
```

the second
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.17-11-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-11-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,2)
kernel /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title Windows Vista/Longhorn (loader)
root (hd1,3)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```
And Save it.

---

### Post by johnmax on 2007-04-28
I changed the boot disk to hdb1 and the system booted OK but when I run df -h I don't show hdb1 but I do when I run gparted. Hdb3 is locked and hdb1 is not.

---

### Post by Najand on 2007-04-28
Run:
```

sudo fdisk -l

```
in the terminal and show me the output.

---

### Post by Najand on 2007-04-28
You booted your system? It is not finished yet... Try to go back to LIVE CD!

---

### Post by Najand on 2007-04-28
And run:```

sudo fdisk -l

``` in the live CD.

---

### Post by johnmax on 2007-04-28
I am live CD now and will run the command

---

### Post by johnmax on 2007-04-28
This is what I get

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount -t /dev/hdb1 /,ny
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ sudo gedit /mnt/etc/fstab
ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$

---

### Post by Najand on 2007-04-28
First of all: you should type:
```
 $ sudo mount -t [COLOR="Blue"]ext3[/COLOR] /dev/hdb1 /mnt
```
Secondly: it is 
```

sudo fdisk -l

```IT IS "L" NOT "ONE".

---

### Post by johnmax on 2007-04-28
ubuntu@ubuntu:~$ sudo mount -t ext3 dev/hdb1 /mnt
mount: special device dev/hdb1 does not exist


Do I enter the second command line. I am operating from the CD.ubuntu@ubuntu:~$ sudo mount -t ext3 dev/hdb1 /mnt
mount: special device dev/hdb1 does not exist

---

### Post by johnmax on 2007-04-28
I made a data entry error. Here is the corrected response

ubuntu@ubuntu:~$ sudo mount -t ext3/ dev/hdb1 /mnt
mount: unknown filesystem type 'ext3/'

---

### Post by Najand on 2007-04-28
Look at it carefully:
The space is after 3, not the slash.
```
[SIZE="4"][COLOR="Blue"] $ sudo mount -t ext3 /dev/hdb1 /mnt[/COLOR][/SIZE]
```

---

### Post by johnmax on 2007-04-28
here are the fdisk results

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9720    78068809    7  HPFS/NTFS
/dev/sda2            9720       13013    26456064    7  HPFS/NTFS
/dev/sda3           13013       13841     6651904    f  W95 Ext'd (LBA)
/dev/sda4           13842       14593     6040440    7  HPFS/NTFS
/dev/sda5           13013       13841     6650880    b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9463    76011516   83  Linux
/dev/hdb2            9944       19458    76416000    7  HPFS/NTFS
/dev/hdb3            9464        9919     3662820   83  Linux
/dev/hdb4            9920        9943      192780    5  Extended
/dev/hdb5            9920        9943      192748+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by Najand on 2007-04-28
Seems you are getting tires.. Wanna a 15-minute break?

---

### Post by johnmax on 2007-04-28
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /mnt
mount: /dev/hdb1 already mounted or /mnt busy
mount: according to mtab, /dev/hdb1 is already mounted on /mnt

---

### Post by Najand on 2007-04-28
OK, 5 more minutes and I hope it will go fine... 
Mount your /dev/hdb1 using the above command.
And the run:
```

$ sudo -s
# grub-install --root-directory=/mnt /dev/sda

```
And copy and paste the result here.

---

### Post by johnmax on 2007-04-28
its late here so lets keep going if possible.

Thanks,

John

---

### Post by Najand on 2007-04-28
Also copy and paste the contents of "/mnt/boot/grub/menu.lst":
```

cat /mnt/boot/grub/menu.lst

```

---

### Post by johnmax on 2007-04-28
do we really want to do sda instead of hdb?

---

### Post by johnmax on 2007-04-28
My bios is set to boot from hdb before sda

John

---

### Post by Najand on 2007-04-28
Well, can you do the following before doing the grub-installer command:
```

$ cat /mnt/boot/grub/device.map

```

---

### Post by johnmax on 2007-04-28
ubuntu@ubuntu:~$ sudo -s
root@ubuntu:~# cat /mnt/boot/grub/device.map
(hd0)   /dev/hdb
(hd1)   /dev/sda
root@ubuntu:~#

---

### Post by Najand on 2007-04-28
Then you were right.
```

$ sudo -s
# grub-install --root-directory=/mnt /dev/hdb

```
And then
```

$ cat /mnt/boot/grub/menu.lst

```
Copy and paste the bottom part which starts with title~~~~~
there must be a few parts.

---

### Post by johnmax on 2007-04-28
First part

root@ubuntu:~# grub-install --root-directory=/mnt /dev/hdb
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hdb
(hd1)   /dev/sda

---

### Post by Najand on 2007-04-28
Sounds nice.... And the second part?

---

### Post by johnmax on 2007-04-28
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Najand on 2007-04-28
Sorry... 
```

$ cat /mnt/boot/grub/menu.lst

```
Seems I am getting tired too.

---

### Post by johnmax on 2007-04-28
I appreciate the help.

Domo

ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
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
# kopt=root=UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Windows Vista/Longhorn (loader)
root            (hd1,3)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

ubuntu@ubuntu:~$

---

### Post by Najand on 2007-04-28
OK, then let us use the grub command:
first
```

sudo -s

```
then ```

grub
```

---

### Post by Najand on 2007-04-28
Then in the grub:
```

> find /boot/grub/stage1

```
You'll get a response like "(hd0)" or in my case "(hd0,2)".

---

### Post by johnmax on 2007-04-28
completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub>

---

### Post by Najand on 2007-04-28
Say it to me when ready!

---

### Post by johnmax on 2007-04-28
(hd0,0)
 (hd0,2)

grub>

---

### Post by Najand on 2007-04-28
Good. Continue with these commands:
```

> root (hd0,0)
> setup (hd0,0)

```
And the 
```

> quit

```
Then edit /mnt/boot/grub/menu.lst agan and change all [COLOR="Red"]/dev/hda3[/COLOR] to [COLOR="Blue"]/dev/hda1[/COLOR]

---

### Post by Najand on 2007-04-28
You there? If you are done, restart your computer. And see which patition is locked.

---

### Post by johnmax on 2007-04-28
This is what I get

root@ubuntu:~# edit /mnt/boot/grub/menu.lst
Warning: unknown mime-type for "/mnt/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
root@ubuntu:~# edit/mnt/boot/grub/menu.lst
bash: edit/mnt/boot/grub/menu.lst: No such file or directory
root@ubuntu:~# edit /mnt/boot/grub/menu.lst
Warning: unknown mime-type for "/mnt/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
root@ubuntu:~#  (hd0,0)
bash: hd0,0: command not found
root@ubuntu:~#  (hd0,2)
bash: hd0,2: command not found
root@ubuntu:~# 
root@ubuntu:~# grub>
bash: syntax error near unexpected token `newline'
root@ubuntu:~#

---

### Post by Najand on 2007-04-28
I meant "edit" as a verb not application... 
```

sudo gedit /mnt/boot/grub/menu.lst

```

---

### Post by johnmax on 2007-04-28
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
default		0

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
# kopt=root=UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

root@ubuntu:~# edit/mnt/boot/grub/menu.lst
bash: edit/mnt/boot/grub/menu.lst: No such file or directory
root@ubuntu:~# edit /mnt/boot/grub/menu.lst
Warning: unknown mime-type for "/mnt/boot/grub/menu.lst" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"
root@ubuntu:~# (hd0,0)
bash: hd0,0: command not found
root@ubuntu:~# (hd0,2)
bash: hd0,2: command not found
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Windows Vista/Longhorn (loader)
root		(hd1,3)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by johnmax on 2007-04-28
Is this right Then edit /mnt/boot/grub/menu.lst agan and change all /dev/hda3 to /dev/hda1 or should it be Then edit /mnt/boot/grub/menu.lst agan and change all /dev/hdb3 to /dev/hdb1

---

### Post by Najand on 2007-04-28
Try to chage all [COLOR="Red"]/dev/hdb3[/COLOR] to [COLOR="Blue"]/dev/hdb1[/COLOR]:
Also change [COLOR="Red"]hd(0,2)[/COLOR] to [COLOR="Blue"]hd(0,0)[/COLOR]
```

the second
# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f3fa4883-b3d8-4b20-9272-abd6e27c216c ro
# kopt_2_6=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

[COLOR="Blue"]title Ubuntu, kernel 2.6.17-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro single
initrd /boot/initrd.img-2.6.17-11-generic
boot

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=[COLOR="Blue"]/dev/hdb1[/COLOR] ro single
initrd /boot/initrd.img-2.6.17-10-generic
boot

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet
boot[/COLOR]

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows Vista/Longhorn (loader)
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title Windows Vista/Longhorn (loader)
root (hd1,3)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```
And Save it.

---

### Post by johnmax on 2007-04-28
saved,
now what?

---

### Post by Najand on 2007-04-28
Did you chage all [COLOR="Red"]/dev/hdb3[/COLOR] to [COLOR="Blue"]/dev/hdb1:[/COLOR]
Also change [COLOR="Red"]hd(0,2)[/COLOR] to [COLOR="Blue"]hd(0,0)[/COLOR]

---

### Post by Najand on 2007-04-28
If you are done and you are usre... Restart your computer and remove CD
Check if the /dev/hdb1 locked or /dev/hdb3?

---

### Post by johnmax on 2007-04-28
both were done.

---

### Post by Najand on 2007-04-28
We are doing it for almost 5 hours... Installing a new ubuntu was much faster... LOL
At least I hope it works.

---

### Post by johnmax on 2007-04-28
Yes all now woks. I do appreciate the help very much.

It was probably a break even proposition as I had already loaded several windows programs into wine and had it Ubuntu configured with numerous features. Please let me know if you ever visit the LA area. 

[email]johnmaxwell1@netscape.net[/email]

---

### Post by Najand on 2007-04-28
Sure.... Thank you too for your patience.... Have a good night!

---

### Post by johnmax on 2007-04-28
Linux is a re-learning experience as i started writing test programs for semiconductors in the early 70's on PDP8 and PDP11 computers using toggle switches and paper tape, Then there was DOS MAC and unfortunately Windows. Thanks again for the learning experience and patients.

Thanks again.

John Maxwell

---

### Post by maniac_X on 2007-04-28
I have to applaud both of you, Najand and johnmax.

johnmax for sticking in there so many hours without once uttering frustration!! \\:D/ 

...and Najand, also for sticking in there so many hours!! You sir, have shown johnmax and others who read this thread the meaning of Ubuntu!

.

---

