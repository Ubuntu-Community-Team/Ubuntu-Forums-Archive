---
title: "Installing Ubuntu in a pc with two hard drives"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by Ferrins on 2008-01-22
Hi everbody!

Let me just say hello to everybody around, I'm totally a newbie on Ubuntu and I'm really looking forward to start using it regulary. Unfortunately, I kinda suck on computer systems and the installation has become quite and issue for me.

The thing is that I have two hard drives. Booting from live cd works great, when I get to the partitions dialog box, both hard drives are detected properly as SCSI (0,0,0) and SCSI (0,1,0). (There's is no mention on master or slave stuff).

Ok then, if I hit the Guided installation I come with a Grub 21 error when rebooting, So the only option left is manual partition. This is what I do:

DISK A - SCSI (0,0,0):
1 partition for swap (1Gb)
1 partition for / as mount point (10Gb)
1 partition for /home (the rest of the disk space)

DISK B - SCSI (0,1,0)
1 partition for swap (1Gb)
1partition for /video* (The rest of the disk space)

*I say video because I can not put another mount point in here, right? 

The result of all this: 
Once I've rebooted Ubuntu doesn't show me the DISK B anywhere, nor even in computer, and the filesystem is well-located but I cannot see a Disk A icon anywhere neither.

So, if you're still reading this I owe you a beer, I really apreciatte your time, and any tip on this, gee thanks!

---

### Post by alphanaut on 2008-01-22
The good thing about linux is it doesnt use drive-letters. Disk A, partition 2 is mounted as root (/) and partition 3 is mounted as /home. Disk B, partition 2 is mounted as /video.
The key is not to think in physical disk, think partitions and mountpoints.


Like so:
/dev/sda2    /
/dev/sda3    /home
/dev/sdb2    /video

If mounted correctly, you should find your second disk, partition 2 in /video.
In nautilus' addressbar type in /video and press <enter>.
In a terminal, type in *cd /video*<enter>.

To check if the partitions is mounted, open up a terminal and type:
*mount*

You will get something like:
[I]/dev/sda3 on / type ext3 (rw,errors=remount-ro,acl)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/mapper/truecrypt0 on /media/sda2 type ext3 (rw)[/I]

If we look closely at this output, we will find that my root (/) is mounted from /dev/sda3
*/dev/sda3 on / type ext3 (rw,errors=remount-ro,acl)*

Did this help?

---

### Post by Ferrins on 2008-01-22
Hey alphanaut thanks for your post!

Well everything is like you said, I did the mount thing and it returned the same data you posted. But now I wonder, and pardon my ignorance, how come I don't see the /video directory anywhere? it doesn't appear on the Computer dialog box, what if I wanna drag something into it? I can't because I don't see it...

Thankx

---

### Post by logos34 on 2008-01-22
post your fstab and fdisk

sudo fdisk -l

cat /etc/fstab

---

### Post by Ferrins on 2008-01-22
Ok, there you go:


sudo fdisk -l
-------------------------------------------------------------------------------------------------------
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2   *         128         735     4883760   83  Linux
/dev/sda3             736        9726    72220207+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x937c7cc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     1028128+  82  Linux swap / Solaris
/dev/sdb2             129        4865    38049952+  83  Linux


cat /etc/fstab
------------------------------------------------------------------------------------------------------------
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd478bc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         127     1020096   82  Linux swap / Solaris
/dev/sda2   *         128         735     4883760   83  Linux
/dev/sda3             736        9726    72220207+  83  Linux

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x937c7cc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         128     1028128+  82  Linux swap / Solaris
/dev/sdb2             129        4865    38049952+  83  Linux


THANKX

---

### Post by logos34 on 2008-01-22
you posted fdisk twice.

---

### Post by Ferrins on 2008-01-22
gee, you're right I'm sorry...

cat /etc/fstab/
---------------------------------------------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ae1c8bc2-cbf2-4978-90ce-c3c11a17f69d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f318aeb4-2726-48b8-be74-3e706560e83b /home           ext3    defaults        0       2
# /dev/sdb2
UUID=4cea3d62-d2d5-4a41-af9f-c4dc2d0ffa3b /video          ext3    defaults        0       2
# /dev/sda1
UUID=3d9d6f22-b5a0-4bb7-8420-d1cf3eb4a89a none            swap    sw              0       0
# /dev/sdb1
UUID=17547f10-ae21-47cb-bcb1-2693199be1aa none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Thanks!

---

### Post by logos34 on 2008-01-22
> # /dev/sdb2
UUID=4cea3d62-d2d5-4a41-af9f-c4dc2d0ffa3b /video ext3 defaults 0 2

entry looks ok.

Click on 'file system' in nautilus, do you see /video in main window?  Can you access it?

As for the desktop icons, /home won't show up there (I have one and it doesn't).  But anything else should.  

sudo gconf-editor

>apps>nautilus>desktop

is 'volumes_visible' ticked?

---

### Post by Ferrins on 2008-01-22
Ok, I see /video in the main window of file system, but I guess that's all right altough I thought since it's a different volume should be put aside, but hey... and volumes-visible is ticked as well, so I guess this is ok? well I'm kinda lost but thanks for your help I truly apreciate :)

---

### Post by logos34 on 2008-01-22
maybe partitions only show up in the side pane (and desktop) when they're mounted at /media (the default place) or /mnt or something.  You could create a new mount point, say /media/video, mount it there and see howit shows up.

---

### Post by Ferrins on 2008-01-24
Why don't we try a different approach to the thread? I mean, I think I'm gonna reinstall Ubuntu again since this seems not to work at all.

What I'd like to see when I browse the Computer dialog box is:
[LIST]
[*]Floppy disk
[*]cd player
[*]dvd burner
[*]80 Gb hard drive
[*]40 Gb Hard Drive
[/LIST]

Just the like if I was browsing My Computer in Windows.

So, for the partitions, how should I do them in order to achieve this?

Thankx again!!!

---

### Post by lswest on 2008-01-24
you can bookmark /video into the side panel of nautilus by dragging it there, and if you want a home icon on your desktop, just make up a launcher for nautilus, or create a symbolic link to it. to create a launcher, the way i did it, is to right-click the gnome panel and choose "add launcher" and give in ```
nautilus /home/[yourusername]/ for home
``` or ```
nautilus /video
``` which creates a launcher on the panel, which you can drag to the desktop, and delete from the panel afterwards. For a symbolic link you can ```
ln -s /home/[yourusername] /home/yourusername]/Desktop/home.sym
``` and for the video link, just swap home with video in the first path, and completely leave out the username, and for the path just change home.sym

---

