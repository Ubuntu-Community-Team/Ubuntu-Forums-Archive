---
title: "unsure how to enable a partition in 6.06LTS"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by glerg on 2007-03-19
As a brand new user (two days) I'm doing well.  However I can't seem to make my /dev/hda2 partition become accessable.  I am unsure about the various commands in the GUI.  (like Access Path, etc)

See the attachment .png for what I am looking at in Disks Manager:

Any help most appreciated!

---

### Post by Death_Sargent on 2007-03-19
command from console is 

```
mount /dev/hda2
```

If that does not work then you might need to edit your fstab.

this will only mount it once

another way to manage partitions and disks is to use the gnome partition manager

```
sudo apt-get install gparted
```

the icon should appear under one of the system submenus

---

### Post by Kobalt on 2007-03-19
Some more info about partitions you might find useful : 
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

---

### Post by dfreer on 2007-03-19
It looks like Disks Manager is no longer available (see [*_this thread_*]("http://ubuntuforums.org/showthread.php?t=325664")), so I'm not quite sure how to mount disks using it. 
  However from your screenshot it looks like all you need to do is create a folder to mount the drive to. Most people would mount it in /media/hda2, although you can mount it anywhere where you have a empty folder. You can create a folder using this command in terminal (you may be able to create a folder with the Disk Manager GUI as well):
```
sudo mkdir /media/hda2
```
  From there, using Disk Manager, mount the drive by entering: 
```
/media/hda2
```
   In the *Access Path:*, and then click the button *Enable*. 
   
   If this doesn't work, you could always mount the partition with this command in terminal:
```
pmount /dev/hda2
```

   Let us know if you have any more problems :)

---

### Post by dannyboy79 on 2007-03-19
you don't need 2 swap partitions for one thing. you could delete 1 of them but make sure you delete the one that fstab is NOT using. post the output from the
**mount**
command (open a terminal and type that in) just paste all of it here so we can get ride of 1 of the swap partitions. 
In linux, there are no drive letters like in windows, there are hard disks (hdx or sdx, the hd is for ide drives and sd is for sata and usb drives that run on the scsi emulation layer. the "x" represents which drive it is, hd**a** is connected to the first ide channel and so on) and partitions (hda1 is the first partition and so on). You need to run a command in a terminal to find out your hard drives and partitions OR you can use the disk manager like you already have. Then it's simply a matter of telling linux where you want a partitions data to show up. This is referred to as a mount point, because you're "mounting" you data in a certain folder or location. There are 2 ways to mount partitions, the manual way and the automatic way. The manual way is done thru the command line using the "mount" command, the automatic way is to update a file called fstab. I have pasted all the neccessary info below from the link that kobalt provided. If you need help with the options in your fstab for what is best, then just post back and inform me what you will be storing on this drive and we can decide on a good location as well as the appropriate options. good luck

Create a Mount Point
Now that the drive is partitioned and formatted, you need to choose a mount point. This will be the location from which you will access the drive in the future. I would recommend using a mount point with "/media." For this example, we'll use the path "/media/mynewdrive" 

  sudo mkdir /media/mynewdrive
  Now we can mount the drive to the mount point. 

  sudo mount /dev/hdd1 /media/mynewdrive   (NOTE: yours would be /dev/hda2 & whatever mount you chose/created)
  If all goes well, you should be able to use your drive at the mount point you chose. 

Mount the Drive
You can choose to have the drive mounted automatically each time you boot the computer, or manually only when you need to use it. 

Automatic Mount at Boot
You'll need to edit /etc/fstab: 

  gksudo gedit /etc/fstab
  Add this line to the end: 

  /dev/hdd1    /media/mynewdrive   ext3    defaults     0        2
(NOTE: yours would again be /dev/hda2 & whatever mount point you chose/created)
  The "2" at the end instructs your system to run a quick file system check on the hard drive at every boot. Changing it to "0" will skip this. Run 'man fstab' for more info here. 

Finally, you need to take ownership of the mount point. Run this command, replacing USERNAME with your username: 

  sudo chown -R USERNAME:USERNAME /media/mynewdrive (NOTE: yours would again whatever mount point you chose/created)

  After rebooting your computer, you should be good to go. 

Manually Mount
Alternatively, you may want to manually mount the drive every time you need it. 

For manual mounting, use the following command: 

sudo mount /dev/hdd1 /media/mynewdrive (NOTE: yours would again be /dev/hda2 & whatever mount point you chose/created)
When you are finished with the drive, you can unmount it using: 

sudo umount /media/mynewdrive (NOTE: yours would again be whatever mount point you chose/created)

GOOD LUCK and welcome to linux

---

### Post by glerg on 2007-03-19
All of you have helped.  I now have something to work with and some good control over that partition.

Linux users seem really helpful, and that sure makes thing lots easier for somebody new.

Best wished to all!

Meantime here is the info that db79 asked me to provide about the 2nd swap file:

mgo@mgo-laptop:~$ mount
/dev/hda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw)
/dev/hda2 on /home/mgo/hda2 type ext3 (rw)
mgo@mgo-laptop:~$

and dannyboy79, thanks for the mini-tutorial.  I'l grab a cup of coffee and spend some time reading that.  It's the most helpful thing yet for me in working with partitions!

---

### Post by dannyboy79 on 2007-03-19
wow, I don't even see it? i wonder if your computer is even using a swap partition? can you post the output from this command?

**sudo cat /etc/fstab** (note: you may or may not need to use sudo, i think for only displaying files owned by root you don't need to use sudo but if it doesn't work without sudo than just use it)

---

### Post by glerg on 2007-03-19
mgo@mgo-laptop:~$ sudo cat /etc/fstab
Password:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
mgo@mgo-laptop:~$


--seems to be there....also my original post had a Disks Manager graphic showing two swap files, which was which kicked up this exchange in the first place.  Additionally, when I ran my partitioning program, it also listed two swap files.

Thanks for your interest.

---

### Post by dfreer on 2007-03-19
Hmmm... your /etc/fstab file looks fine to me. Perhaps your extra swap file is mounted in /etc/mtab? Try a *sudo cat /etc/mtab*. It's likely that this isn't a critical problem, but it's interesting why it's listing 2 swap files in both Disk Manager and your partition program. What does it have listed for both swap files in those programs (e.g. /dev/hda6)?

---

### Post by dannyboy79 on 2007-03-19
as long as your partitioning program said that the other swap was something other than hda6, you can delete that partition using gparted (the one that ISN'T hda6 as that;s your current swap partition for your install) and grow one of your other partitions to use the space. i mean if it's only  like 256mb than maybe you could just ignore but it may come down to not being able to save a file if that's all the space you have left, just being wasted by it being called swap. it's obviously up to you. there is always a risk of gparted messing something up as it is resizing a partition with data on it. if you have done anything yet than maybe back that stuff onto cd or dvd or a partition other than the one you are going to grow. also, it might be safest to do the deleting and growing using the live cd gparted, that way the partition your're growing isn't mounted. good luck in whatever you decide.

---

