---
title: "[SOLVED] format second hard drive"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by philipluna66 on 2008-04-12
I have just installed Ubuntu 7.10 on my old desktop. I have installed it on HD0 8.5 gig. I also have another drive in my desktop HD1 13.5 gig which I was hoping to use to store my music and photos etc. The problem is I used to have my Ubuntu6.06 on this drive and the folders are still there. I need to remove everything and set up folders for my music etc so it will automatically save to there. Is it possible and how.Thank you

---

### Post by SnakeHips on 2008-04-12
firstly so we know what we are looking at would you post the output from the following commands.

```
sudo fdisk -l
```

and 

```
mount
```

---

### Post by philipluna66 on 2008-04-12
philip@philip-desktop:~$ sudo fdisk -1
[sudo] password for philip:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
philip@philip-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)
philip@philip-desktop:~$

---

### Post by SnakeHips on 2008-04-12
ok nearly there...
thats the letter l at the end of the code (L for List)
so 

```
sudo fdisk -l
```

you should see something like this:


```
pete@desk:~$ sudo fdisk -l
[sudo] password for pete: 

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb95b67cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1207     9695196   83  Linux
/dev/sda2            1208        1268      489982+  82  Linux swap / Solaris
/dev/sda3            1269        7771    52235347+  83  Linux
/dev/sda4            7772        8379     4883760    5  Extended
/dev/sda5            7772        8379     4883728+  83  Linux

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8b1aa828

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7476    60050938+   c  W95 FAT32 (LBA)
```

---

### Post by polmir on 2008-04-12
**philipluna66** correct your post, Wrap ```
 tags around text you copy to forum from terminal.

Type in terminal:
[CODE]sudo fdisk -l  /dev/hda
sudo fdisk -l /dev/hdb
```
and post output.

**-l --- it is small letter ,,L''**

---

### Post by philipluna66 on 2008-04-12
philip@philip-desktop:~$ sudo fdisk -l
[sudo] password for philip:

Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007bca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/sdb: 13.6 GB, 13672931328 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd14a62bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1590    12771643+  83  Linux
/dev/sdb2            1591        1662      578340    5  Extended
/dev/sdb5            1591        1662      578308+  82  Linux swap / Solaris
philip@philip-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
philip@philip-desktop:~$ 

Hope this is Ok thanks

---

### Post by SnakeHips on 2008-04-12
Ok ,here's the disk you want to wipe your data from:

```
Disk /dev/sdb: 13.6 GB, 13672931328 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd14a62bf
```

but..........did you un-mount this drive ?

```
philip@philip-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
[COLOR="Red"]/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)[/COLOR]
```

---

### Post by philipluna66 on 2008-04-12
OK now you have TOTALLY confused me I am assuming I have to put in a command to format /dev/sdb: Being slow hear what do I put in to format it. As for the second bit I havent un mounted it wouldnt know how. But when all is ok I want to be able to save photos etc to this drive

---

### Post by sisco311 on 2008-04-12
you can use gparted to format your disk(sdb)
my suggestion is to format the whole drive to one ext3 partition.

to install gparted[ click here]("apt:gparted")
or type
```
sudo aptittude install gparted
```in the terminal.

to mount the partition you need a mount point
```
sudo mkdir /media/music
```or mount it in your home directory
```
mkdir ~/music
```edit the fstab:
```
gksu gedit /etc/fstab
```and add this line:
> /dev/sdb1 /media/music       ext3    defaults        0       2or
> /dev/sdb1 /home/**yourusername**/music      ext3    defaults        0       2mount the partition:
```
sudo mount -a
```change the owner of the partition to get write permission
```
sudo chown -R yourusername:yourusername /media/music
```

---

### Post by SnakeHips on 2008-04-12
^^^ beat me to it :-)

I didnt mean to confuse , just needed to clearly identify the exact drive/partitions you want to wipe clean. Looks like these are the partitions you are after.

```
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 1590 12771643+ 83 Linux
/dev/sdb2 1591 1662 578340 5 Extended
/dev/sdb5 1591 1662 578308+ 82 Linux swap / Solaris

```

It may be easier for you with a GUI application ,if you have'nt already woulld you install Gparted ,you will find this in system/admin/synaptic package manager.......search for "gparted"

Once installed you can run this from terminal with 

```
gksudo gparted
```

...and set your partitions as you want. please be careful and select the correct drive /dev/sbd/ and as always check to ensure there is nothing on the partition(s) you want to keep.

Then its the case of creating a new partition(s) with maybe a mount point of /mnt/music?

hope it helps

---

### Post by philipluna66 on 2008-04-12
Thanks for the info did everything you suggested all went well This is what I have now
Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007bca8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/sdb: 13.6 GB, 13672931328 bytes
255 heads, 63 sectors/track, 1662 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd14a62bf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1590    12771643+  83  Linux
/dev/sdb2            1591        1662      578340    5  Extended
/dev/sdb5            1591        1662      578308+  82  Linux swap / Solaris
philip@philip-desktop:~$ 
Just one thing In my computer my second hard drive isnt showing??? And if I want to create folders on this drive do I follow the instructions as before just change the file name. Thinking of photos

---

### Post by SnakeHips on 2008-04-12
Your last post shows /dev/sbd unchanged. Have you worked this out now or still need some help ?

---

### Post by philipluna66 on 2008-04-12
I couldnt find the second drive in computer but I rebooted and hay presto it apeared. I also created a folder for photoes in the as well. THANKS

---

### Post by SnakeHips on 2008-04-12
:) Good to hear you got it sorted....would  you mark this post as solved..

---

### Post by philipluna66 on 2008-04-13
How do I mark As solved ?

---

### Post by SnakeHips on 2008-04-13
Have a look around your original post somewhere ,,i'm not sure...

---

