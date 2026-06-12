---
title: "Dual boot --- Two linux systems"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by greenwom on 2005-09-22
Ok so I love ubuntu but I wanted to try a new distro just to compare.

On a new (to me) box I installed fedora core and then I tried to install ubuntu after that, I placed ubuntu on a different partition (if I got it right :) )

When I did the first reboot, I was waiting to see the grub loaded show me two options.....

Nothing, just ubuntu?

how would I look at the other partition to see if fedora is still there

or 

what's the right way to do this.

I'm going to do a system rescue wipe and start with two fresh partitions and let the installers set it up (if I don't get a much response)

Can the systems share a swap? and is there any other concerns I should have??

---

### Post by Kapre on 2005-09-22
[QUOTE=greenwom]Ok so I love ubuntu but I wanted to try a new distro just to compare.

On a new (to me) box I installed fedora core and then I tried to install ubuntu after that, I placed ubuntu on a different partition (if I got it right :) )

When I did the first reboot, I was waiting to see the grub loaded show me two options.....

Nothing, just ubuntu?

how would I look at the other partition to see if fedora is still there

or 

what's the right way to do this.

I'm going to do a system rescue wipe and start with two fresh partitions and let the installers set it up (if I don't get a much response)

Can the systems share a swap? and is there any other concerns I should have??[/QUOTE]

Greenworm - I would assume that when you installed Fedora, it was working. Just would like to know if you make a new partition when Ubuntu was installed? I asked this because during the install process, Ubuntu will ask you questions regarding where you would like to install, I guess you overwrote the partition where Fedora was installed.

If you installed breezy, you can click on System--->Administration--->Disk and you'll see what partition(s) are present. 

I too have a triple boot (XP, Fedora4 and Ubuntu) but I have 2 HD. HD1 is used by XP and Fedora and the HD2 is Ubuntu.

K

---

### Post by greenwom on 2005-09-22
I took note of what partition came up and then wrote ubuntu into the opposite?

I guess I over wrote it.  

I've got hoary installed on the box now, and I want to install fedora.

When I started at this point last time it overwrote ubuntu... and then the other way around. (feel'n dumb at this point)

Can the systems share a swap?

---

### Post by drogoh on 2005-09-22
I know this reply is meaningless and off-topic but instead of dual or triple booting, why not stick with one operating system and just play in VMware?  It's not *identical* to your hardware but I notice no difference between the three virtual machines (Solaris 10 x86 / Ubuntu 5.10 / Lunar Linux 1.5.1) I have running in VMware on an XP Media Center Edition host.


And to answer the question about "sharing swap", yes.

---

### Post by aysiu on 2005-09-22
Did you install Grub to the MBR?
If not, you can just copy the appropriate entry from one /boot/grub/menu.lst to the other one (you must use sudo to do this).

---

### Post by greenwom on 2005-09-23
Well this has become a small challenge (and a chance to learn)
I continually have had trouble with partitions, I need to read up up this is what I'm trying right now.

I'm installing used the install CD to wipe off the old partions, and split the drive in three (hda1, swap, and free space)

I'm installing Fedora on the free space, Anaconda want to set up LVM (I need to learn about this) and then the partion hda3.

I then plan to reinstall Ubuntu in Hda1.

hope it works, if I'm way off base let me know.


Either way if I can't get it to work I'm keeping ubuntu.  I did however see a few Gnome apps in Fedora that I'll be installing on my regular machine, like the Visio clone.

---

### Post by greenwom on 2005-09-24
[Well I'm trying to get to the other partiton to see the grub menu.lst so that I can get the other os up ( I hope it's still there)

here's what I got

[COLOR=Red]mike1@ubuntu3:/media/fedora$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  1.6G   16G   9% /
tmpfs                  62M     0   62M   0% /dev/shm
/dev                   18G  1.6G   16G   9% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
mike1@ubuntu3:/media/fedora$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2376    19085188+  83  Linux
/dev/hda2            2423        2473      409657+  82  Linux swap / Solaris
/dev/hda3            2474        2486      104422+  83  Linux
/dev/hda4            2487        4865    19109317+   5  Extended
/dev/hda5            2487        4865    19109286   8e  Linux LVM
mike1@ubuntu3:/media/fedora$[/COLOR]

How do I mount these drives?  I tried to follow a forum on it but I'm a little lost.

---

### Post by bored2k on 2005-09-24
Please refer to my instructions at: [http://ubuntuforums.org/showpost.php?p=368701&postcount=3](http://ubuntuforums.org/showpost.php?p=368701&postcount=3)

Just change hda2 for whatever you want (hda4 I think).

---

### Post by greenwom on 2005-09-24
]
[COLOR=Red]mike1@ubuntu3:~$ sudo mount -a
mount: /dev/hda5 already mounted or /media/fedora busy[/COLOR]

Well this is where I'm at know, I added the line as follows

[COLOR=Green]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda5       /media/fedora   ext3    umask=000       0       0[/COLOR]

I've tried a couple of things but no luck, any insight?

---

### Post by bored2k on 2005-09-24
Help me, help you. What /dev/hd do you want to mount (at least tell me that much).

[QUOTE=The Guidelines]Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.[/QUOTE]The colors man, they're not nice on the eye.

---

### Post by bored2k on 2005-09-24
If what you want is hda5, you NEED to 
```
sudo mkdir /media/fedora
``` and then do the stuff first. Instead of the lines for FAT in fstab, add
```
 /dev/hda5 /media/fedora ext3 defaults,errors=remount-ro 0 1
```

---

### Post by greenwom on 2005-09-26
[QUOTE=bored2k]If what you want is hda5, you NEED to 
```
sudo mkdir /media/fedora
``` and then do the stuff first. Instead of the lines for FAT in fstab, add
```
 /dev/hda5 /media/fedora ext3 defaults,errors=remount-ro 0 1
```[/QUOTE]

Thanks, I had the file system right just not the other options, your help was greatly appreciated.

---

### Post by Jad on 2005-11-18
actually i've same problem
```

sudo mount -a
mount: /dev/hdb2 already mounted or /media/fedora busy
```


/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              36G   27G  8.0G  77% /
tmpfs                 380M     0  380M   0% /dev/shm
tmpfs                 380M   13M  367M   4% /lib/modules/2.6.12-9-686/volatile[/CODE]

```
sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4772    38331058+  83  Linux
/dev/hda2            4773        4865      747022+   5  Extended
/dev/hda5            4773        4865      746991   82  Linux swap / Solaris

Disk /dev/hdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14        2482    19832242+  8e  Linux LVM
```

---

### Post by adam.skinner on 2005-11-19
Jad, I'm essentially in the same boat as you are:

```

root@elijah:/mnt# [COLOR="Blue"]ls -l /mnt ; mount -t ext3 /dev/hdb5 /mnt/d2 ; fdisk -l[/COLOR]
total 4
drwxrwxrwx  2 root root 4096 2005-11-19 06:00 d2
[COLOR="Red"]mount: /dev/hdb5 already mounted or /mnt/d2 busy[/COLOR]

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3187    25599546    c  W95 FAT32 (LBA)
/dev/hda2   *        3188       14215    88582410   83  Linux
/dev/hda3           14216       14593     3036285    5  Extended
/dev/hda5           14216       14593     3036253+  82  Linux swap / Solaris

Disk /dev/hdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        4870    38869267+   5  Extended
/dev/hdb5              32        4870    38869236   8e  [COLOR="Green"]Linux LVM[/COLOR]

```

I suspect I'm unable to mount it because it's an LVM (same as you).

Here's the deal - I've got it working:
Firstly, the source thread with the relevant info is here: [http://clemsonlinux.org/Forum/viewtopic.php?p=1257](http://clemsonlinux.org/Forum/viewtopic.php?p=1257)

Follow those instructions.  I didn't catch on quite as quickly as I should have though.  Here's the part that threw me:

The stuff that you see in /dev/mapper, once it's activated via lvchange -a, is now available in /dev/<mapname> (in my case, this was /dev/Ubuntu).  Then you'll just want to mount those whereever you want them (ie sudo mount /dev/Ubuntu/root /mnt/d2)

Here's my console log:
> 
root@elijah:/mnt# lvdisplay
  --- Logical volume ---
  LV Name                /dev/Ubuntu/root
  VG Name                Ubuntu
  LV UUID                ChuNFX-MEOX-6jOO-U9Mb-tg6z-EhI2-2nyn5Y
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                35.59 GB
  Current LE             9112
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0

  --- Logical volume ---
  LV Name                /dev/Ubuntu/swap_1
  VG Name                Ubuntu
  LV UUID                C4iS6f-RmcT-f7T5-kJvt-57r0-zPpl-fP6hRB
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                1.47 GB
  Current LE             377
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:1

root@elijah:/mnt# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "Ubuntu" using metadata type lvm2

root@elijah:/mnt# vgchange -a y
  2 logical volume(s) in volume group "Ubuntu" now active

root@elijah:/mnt# ls /dev/Ubuntu/
root  swap_1

root@elijah:/mnt# mount /dev/Ubuntu/root d2

root@elijah:/mnt# ls d2
bin    debootstrap  home        lib         mnt   root  sys  var
boot   dev          initrd      lost+found  opt   sbin  tmp  vmlinuz
cdrom  etc          initrd.img  media       proc  srv   usr


Enjoy!  I hope this helps.

---

