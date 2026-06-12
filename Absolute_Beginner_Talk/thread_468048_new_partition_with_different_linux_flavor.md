---
title: "new partition with different linux flavor"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by sgargabonzi on 2007-06-08
Hi, I am a newbie. I have a laptop with 50GB hard drive.

I have 30 GB with Windows XP SP2 and 20 GB with Ubuntu. At startup grub let me correctly choose which OS to load.

Now i would like to dedicate some space to Centos, a Redhat clone. I would like Centos to take some of the space currently used by Ubuntu, so to have a partition table like:

Windows --> 30 GB
Ubuntu --> 10 GB
Centos --> 10 GB

I don't want to harm any current feature or data present in my Windows and Ubuntu installations.

Can I just run the Centos image CD, and it will guide me through handling this or shall i need to make some preliminary operations?  

I know I can look this up either on Centos or Linux sites in general  but thought you guys can give me quick tips to begin with the right step. 

If you need I will send you more info. Thank you very much,

Sgarga.

---

### Post by ghost_ryder35 on 2007-06-08
i'd like to do this setup too, however just Ubuntu and Fedora maybe Debian too ;)

---

### Post by sgargabonzi on 2007-06-08
yep, thats' a nice configuration too. Reason Im installing Centos is I want to feel what is like a red hat clone after I got familiar with Ubuntu.

Anyone with tips to start with the right steps? Do I need to prepare some disk space prior to the Centos installation? 

Thanks,

Sgarga

---

### Post by louieb on 2007-06-08
Just a few thoughts. The two Linux OSes can use the same swap partition. Use the GParted live CD to shrink your current Linux partition and create partition(s) for the other Linux(s). You will need to use the manual partitioning option when you install the second Linux OS. 
When I first started had a old P3 with a 40gig drive at one time had a half dozen distros on it. When you install the 2nd 3rd ... distro have then install there boot loader (most use GRUB or LILO) in the boot sector of their installed  partition and modify the GRUB configuration file of the 1st distro to use the chainloader or configfile option to boot the other distro(s) 

Check out the [Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/") for configfile and chainloader and general dual boot how to stuff.

---

### Post by floke on 2007-06-08
watch out though - some distros - eg sabayon - will not recognise other Linuxes, meaning that you will have to copy over the old grub entries into the new grub.

---

### Post by sgargabonzi on 2007-06-09
Hi guys,

thanks a lot.

I managed to set everything up yesterday night and Im only reading you today but is still very inetersting.

I proudly attach a screenshot of my final grub menu! Prior to reading your suggestions I did not know about Gparted so, could not manage to create space for a new partitions by shrinking the existing ones. So I backed up my Ubuntu stuff and formatted. Then I proceed and installed Centos and Ubuntu again and ended up with a nice 30GB Windows - 12GB Ubuntu - 600MB Swap - 8 GB Centos. So the Swap partition is one as you recommended and will serve the active Linux OS.

While the chainloader pointing to Windows has been working fine all the time I had the problem you mention of the Grub file not pointing correctly to the kernel of the other distribution so I had to copy the path from the Centos Grub file (grub.conf) to the Ubuntu Grub file (menu.lst) and now everything is nicely OK.

There is a detail Im not able to explain: If I load  Ubuntu I can browse the whole HD, including the windows and Centos partitions although I can't delete or create files there. But I can copy and paste in the Ubuntu partition. Instead from Centos, I can only browse the Centos partition. 
I remember that with the former configuration, Windows - Ubuntu, I could not browse windows file from Ubuntu. So this was a nice surprise, but I am not sure wha ti did differently..

Anyway - cool! 

Sgarga

---

### Post by louieb on 2007-06-09
:guitar:Linux contains a file that defines which partitions are mounted and boot time.** /etc/fstab **compare the centos version with the ubuntu version.  do [ Linux - Google Search]("http://www.google.com/linux") on  **fstab ** Don't get throne off by the the fact that Ubuntu starting with Edgy uses uuid to define partitions. and Centos probally (i'm not sure) uses the /dev/hda# to refer to partitions.

---

### Post by sgargabonzi on 2007-06-09
This is the Centos /etc/fstab file:

```
LABEL=/                 /                       ext3    defaults        1 1
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
LABEL=SWAP-hda3         swap                    swap    defaults        0 0
```
And this is the Ubuntu /etc/fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda4
UUID=e94ad9ec-46be-4de6-8024-28695ec98248 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=04DC1A06DC19F2A2 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=06a18426-3883-49ed-84c4-b6e710d4c7ed /media/hda2     ext3    defaults        0       2
# /dev/hda3
UUID=858616b3-6ca4-49b8-812e-ffba5b1be7d4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Moreover in Ubuntu, this is the output of the command df  :

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda4             13622828   2542552  10388280  20% /
varrun                  249460        80    249380   1% /var/run
varlock                 249460         0    249460   0% /var/lock
procbususb               10240       136     10104   2% /proc/bus/usb
udev                     10240       136     10104   2% /dev
devshm                  249460         0    249460   0% /dev/shm
lrm                     249460     17580    231880   8% /lib/modules/2.6.17-10-generic/volatile
/dev/hda1             34812820   6654664  28158156  20% /media/hda1
/dev/hda2              8924660   3532828   4931172  42% /media/hda2   
```

And this is the output of sudo fdisk -l /dev/hda :

```
Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4334    34812823+   7  HPFS/NTFS
/dev/hda2            4335        5481     9213277+  83  Linux
/dev/hda3            5482        5557      610470   82  Linux swap / Solaris
/dev/hda4            5558        7280    13839997+  83  Linux
```


So it appears that 
/dev/hda1 is the Windows partition and is mounted on /media/hda1. 
/dev/hda2 is the Centos partition and is mounted on /media/hda2.
/dev/hda3 is the swap partition not mounted.
/dev/hda4 is the Ubuntu partition and is mounted on /.

Is this correct ?  Thanks for your hint!

---

