---
title: "Accessing different drives"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-03
Is there a way of changing things so I can mount the drives in the screen shot without mucking up my Ubuntu or XP installations.
When I installed Ubuntu I used the automaticre-partitioning feature of Gparted in the install process on the Live CD.
If I ain't making enough sense do let me know and I will try and give more information if you need it.
 I want to be able to access at least one of these drives to browse and edit stored Web pages. I keep a folder with edited versions of ebay pages I am interested in and my other inetrests like vintage radios.
Off topic: Is there a equivalent of Front Page Editor in Ubuntu?

---

### Post by Skrynesaver on 2007-04-03
could you post the output of the ```
mount
``` command

---

### Post by Neil Purling on 2007-04-03
As requested:

neil@neil-desktop:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
neil@neil-desktop:~$

---

### Post by mikeyphi on 2007-04-03
Looks as though the other drives need to be mounted!
See what happens after you type the following into the Terminal

Code:
sudo mount -a



(you'll be asked for your password)

---

### Post by Skrynesaver on 2007-04-03
If that doesn't work could you return the output of ```
cat /etc/fstab
```

---

### Post by antoz on 2007-04-03
M:\ubuntu\MountingWindowsPartitions - Community Ubuntu Documentation.htm

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

[M:\ubuntu\MountingWindowsPartitions - Community Ubuntu Documentation.htm]("M:\ubuntu\MountingWindowsPartitions - Community Ubuntu Documentation.htm")

---

### Post by Neil Purling on 2007-04-04
Antoz: Those posted links don't work!

---

### Post by Neil Purling on 2007-04-04
I have had to do a re-installbecause the Windows XP installation was corrupt.
I have a 250Gb HDD as Master  and a 20Gb as Slave.
I have re-installed XP. That was fun, NOT!

I wish you could get a smilie where its mouth is covered with 'CENSORED' for us to put in place of a cuss word or something else that shall not be mentioned in a polite forum. I would havehad use for it last night!

So we start again. I need to access the Windows partitions.

'mount' command shows:
neil@neil-desktop:~$ mount
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/fd0 on /media/floppy type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
neil@neil-desktop:~$
neil@neil-desktop:~$

I will do the other suggested commands soon.

---

### Post by Neil Purling on 2007-04-04
More use of terminal:

neil@neil-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
neil@neil-desktop:~$


Suggestions welcomed..............

---

### Post by Skrynesaver on 2007-04-04
```
fdisk -l
``` would also be useful as this will tel us where the windows partitions are, (their device names).  We'll then add these devices to your /etc/fstab file.
Not really a GUI user so could someone teill me if  there's a nice GUI front end for this process, not sure if new users need to be exposed to the arcana of vol_id.

---

### Post by ububaba on 2007-04-04
I have four drives.  Sda and hdb both have Ubuntu on them while sdb and sdc have XP.
Both Sda and hdb Ubuntu drives are not visible/(mounted properly?).  This is the result 
of *sudo fdisk -l*. OS is on sda drive. I keep telling myself, pretty soon I will solve the problem
but that's just self-deception!

[COLOR="RoyalBlue"]
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4159    33399135    f  W95 Ext'd (LBA)
/dev/sdb2   *        4160       10533    51199155    7  HPFS/NTFS
/dev/sdb3           10534       10794     2096482+   7  HPFS/NTFS
/dev/sdb4           10795       16709    47512237+   7  HPFS/NTFS
/dev/sdb5               2        4159    33399103+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2        1278    10257502+   f  W95 Ext'd (LBA)
/dev/sdc2   *        1279        5745    35881177+   7  HPFS/NTFS
/dev/sdc3            5746        6006     2096482+   7  HPFS/NTFS
/dev/sdc4            6007       19457   108045157+   7  HPFS/NTFS
/dev/sdc5               2        1278    10257471    7  HPFS/NTFS

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       23944   192330148+  83  Linux
/dev/hdb2           23945       24321     3028252+   5  Extended
/dev/hdb5           23945       24321     3028221   83  Linux
[/COLOR]

---

### Post by Skrynesaver on 2007-04-04
Did you take a look at the link Antoz posted earlier in this thread?
[SIZE=-1]users.bigpond.net.au/hermanzone/p10.htm

You need to edit your fstab to mount these permanently, first off though
```

sudo mkdir /mnt/W95.1
sudo mount -t vfat /dev/sdb1 /mnt/W95.1

```[/SIZE]```
[SIZE=-1]ls /mnt/sdb1 
[/SIZE]
```[SIZE=-1]

Do you see the contents of your W95 filesystem?
Ok now we need to make this a permanent feature on load.
```
gksu gedit /etc/fstab
```and add the following line
```

/dev/sdb1   /mnt/W95.1   vfat   defaults  0  0

```Save and exit, this will mount the partition on reboot.

Notes: 
  1)Substitute a name more meaningful to you than W95.1
  2)An identical process can be carried out on the other W95 drive (/dev/sdc1)
  3)The only difference with NTFS partitions is that the mount type is ntfs
ie
```

sudo mkdir /mnt/NTFS.1
sudo mount -t ntfs /dev/sdb2 /mnt/NTFS.1

```
rinse and repeat ;)
[/SIZE]

---

### Post by Neil Purling on 2007-04-04
This is what you are after....

neil@neil-desktop:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16704   134174848+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1310    10522543+   7  HPFS/NTFS
/dev/hdb2   *        1311        2384     8626905   83  Linux
/dev/hdb3            2385        2434      401625    5  Extended
/dev/hdb5            2385        2434      401593+  82  Linux swap / Solaris

---

### Post by Neil Purling on 2007-04-08
How do I 'unlock' these drives with both read and write permission?

---

### Post by Neil Purling on 2007-04-08
I don't know if this is also relevant, but here it is anyway.

neil@neil-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16704   134174848+   7  HPFS/NTFS

Disk /dev/hdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1310    10522543+   7  HPFS/NTFS
/dev/hdb2   *        1311        2384     8626905   83  Linux
/dev/hdb3            2385        2434      401625    5  Extended
/dev/hdb5            2385        2434      401593+  82  Linux swap / Solaris
neil@neil-desktop:~$
neil@neil-desktop:~$

---

### Post by Neil Purling on 2007-04-13
There are two actual physical hard discs inside my PC. There is one with XP on it (Master) referred to as /dev/hda1.
The Slave is  /dev/hdb1.
As I have seen the drives in 'Computer' why can't I mount them.
I definitely need to be able to mount /dev/hdb1 and enjoy full read and write permissions.
I am sure that using terminal is like second-nature to you but right now I feel like a total idiot.
I just hope this is helpful.

neil@neil-desktop:~$ sudo mount /dev/hda1
mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab


neil@neil-desktop:~$ sudo -s /etc/fstab
/etc/fstab: line 4: proc: command not found
/etc/fstab: line 5: /dev/hdb2: Permission denied
/etc/fstab: line 6: /dev/hdb5: Permission denied
/etc/fstab: line 7: /dev/hdc: Permission denied

---

### Post by Neil Purling on 2007-04-13
I have created a directory with mkdir command in Terminal.
Q. How do I delete one's I no longer need?
I have got the drive //dev/dhb1 to mount in the required directory.
I see the folders of the slave drive XP knows as D:/.
I enter Terminal again and type 'gedit /etc/fstab'

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1	/mnt/NTFS	ntfs	defaults	0	0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

As you see the insert to mount /dev/hdb1 on start-up.

However.... I get a rude message when I try and browse the NTFS folder "The folder contents could not be displayed. You do not have the permissions necessary to view contents of NTFS"

So.. What did I do wrong? 
Is it possible to change the permissions?


Can you can log on as root when it prompts for user name during the boot and change user after you're done.

Im' tired it,s 01:20 hrs here, which is 3 hours past when I usually hit the sack and I am very pissed off. Hopefully you will have the answers for me when I rejoin the land of the living.

---

### Post by antoz on 2007-04-14
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

I am not really in a position to give advice as to what your problem is but I think if you can not access a particular partition it is propably not mounted. Also once you mounted the partition you have to add it to the fstab so it mounts everytime you boot. Check the links your answer may be there.A
PS: I checked the links they are working.

Edit: if you check on hermanzone's link all the commands are there and if you add your partition to the fstab you can the mount them by using  [B]sudo mount -a
[/B]

---

### Post by Neil Purling on 2007-04-14
The drive I wanted was mounted but permission denied to view it. I followed the advice in this thread: [http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS](http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS).
It's sorted. I can now write to the Slave or D:/ drive as Windows calls it (/dev/hdb1).
I have saved a ebay page to there, see screenshot.
All it took was some lost sleep and foul language. I am now going to save the threads  so if I can get the hang of simple web page editing and installing rpm files I am going to be in a position to wipe Bill Gates's foulness from my hard disc.
But that is going to be another story.

---

