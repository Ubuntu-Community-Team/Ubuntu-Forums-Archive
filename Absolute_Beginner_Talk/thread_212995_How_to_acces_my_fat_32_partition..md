---
title: "How to acces my fat 32 partition."
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-07-10
Well, I just made myself a fat32 partition, so I can share my files between my ubuntu, and windows install. The thing is that I cant acces it from Ubuntu, I an acces it from Windows perfectly fine, but not from ubuntu. When I click at it, under the mashine menu it just says. That I cant mount the selected archive. So does anyone know, how I can acces it from Ubuntu?

---

### Post by aysiu on 2006-07-10
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Susan.Desanco on 2006-07-10
While I have definitely in the past found the guides by aysiu to be extremely useful, I have read -- and do not understand much at all -- of the guide mentioned above.  I really appreciate all the work that experts put into helping us newbies, but this one has perplexed me.

I'm in the same boat as the original poster.  I have a nice FAT32 partition created, but don't know how to use it from Ubuntu.

The linked guide mentioned above seems to jump right into several "levels above" my understanding, and perhaps many other beginning Ubuntu users as well.  For instance, the first sentence starts "If you already have your Windows partitions mounted (but with the wrong permissions) ..."  So that leaves me wondering what a mount is, whether I have my Windows partition mounted, whether I have the wrong permissions, and what the correct permissions should/would be.

So I hope someone can help me gain access to my FAT32 partition.  I don't want to be throwing around a bunch of commands regarding partitions/mounting/hard drive stuff and not know or understand what I am doing.

I really appreciate any help on how I can suit up my FAT32 partition so that I can access it from Ubuntu.  Thanks, and here is an image showing my fdisk -l printout:   [B][http://tinyurl.com/kohaz](http://tinyurl.com/kohaz)

.
[/B]

---

### Post by erniewinner on 2006-07-10
i'll jump in with my limited knowledge... if you can see an icon for the disk it's mounted. the first posters wasn't. i learnt a simple command from one of asyiu... got to the terminal type:

gksudo nautilus

a window will open pick the fat 32 drive and drop files you want on to it. and it will let you copy your stuff there... you would need to do this everytime you want to put stuuf on that disk. once the terminal window is closed the disk is no longer writeable... cool! 8)

---

### Post by aysiu on 2006-07-10
As far as I know, the default mounting behavior in Ubuntu mounts Windows but in a way that's totally useless--you can't read from or write to the partition. That's what I mean by incorrectly.

In terms of understanding mounting in general--a mounted partition is basically one that's available for use. Where it's mounted is where you can use it. So the partition may exist at /dev/hda1, but you can't just go to /dev/hda1 to access the data there. You have to mount it somewhere else--/media/hda1, for example, or /windows or /music. There has to be some folder you go where you can see the contents of /dev/hda1.

You need to know where you partition exists (/dev/hda1, for example)

You need to make a directory where this partition will be accessible (/windows, for example)

Then you need to tell Ubuntu where the location is, the mount point is, and what mount options you want. That's where the editing of the /etc/fstab file comes in.

```
/dev/hda1 /windows vfat iocharset=utf8,umask=000 0 0
```

/dev/hda1 - location
/windows - where to access the location
vfat - filesystem type (FAT32)
iocharset=utf8,umask=000 0 0 - read/write for everyone

---

### Post by erniewinner on 2006-07-10
:-D i gotta say i actually like the fact that the disk is "locked" after i've copied my stuff to it. seems like a good idea to me...

---

### Post by Geezle on 2006-07-10
I have an odd twist on this problem.  I'm running Dapper after running Breezy Badger for some time, so I've already figured out how to mount my two FAT32 drives.  The problem I'm having now is that it doesn't work.  I've edited my /etc/fstab file to mount the two drives, but when I boot up, the drives are not mounted.  If I manually mount them using the mount -a command I get the following error: 
mount: /dev/hdc already mounted or /media/hdc busy
mount: /dev/hdd already mounted or /media/hdd busy

and when I try to unmount them I get the following errors:
jay@jay-desktop:~$ sudo umount /dev/hdc
umount: /dev/hdc: not mounted
jay@jay-desktop:~$ sudo umount /dev/hdd
umount: /dev/hdd: not mounted

Now the odd thing is that I can still get read only access to the drives by manually going into my System > Accessories > Disks and assigning a path and enabling the partitions.

I'm really confused on this one, so any help would be greatly appreciated.

---

### Post by aysiu on 2006-07-10
geezle, can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Geezle on 2006-07-10
> **aysiu said:**
> geezle, can you post the output of these three commands? ```
sudo fdisk -l
cat /etc/fstab
df -h
```
```

jay@jay-desktop:~$ sudo fdisk -l

Disk /dev/hda: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         929     7462161   83  Linux
/dev/hda2             930         973      353430    5  Extended
/dev/hda5             930         973      353398+  82  Linux swap / Solaris

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2491    20008926    5  Extended
/dev/hdc5               1        2491    20008894+  83  Linux

Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd2               2        7297    58605120    f  W95 Ext'd (LBA)
/dev/hdd5               2        1058     8490321    b  W95 FAT32
/dev/hdd6            1059        7297    50114736    b  W95 FAT32

jay@jay-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/hdc      vfat    iocharset=utf8,umask=000  0    0
/dev/hdd        /media/hdd      vfat    iocharset=utf8,umask=000  0    0

jay@jay-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             7.1G  6.3G  377M  95% /
varrun                252M   80K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  140K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-25-386/volatile

```

---

### Post by aysiu on 2006-07-10
Make sure these directories exist (if you get an error that they already exist, that's fine): ```
sudo mkdir /media/hdc
sudo mkdir /media/hdd
``` Make sure your partitions are unmounted ```
sudo umount /dev/hdd5
sudo umount /dev/hdd6
``` Back up and edit your /etc/fstab ```
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Change these two lines ```
/dev/hdc        /media/hdc      vfat    iocharset=utf8,umask=000  0    0
/dev/hdd        /media/hdd      vfat    iocharset=utf8,umask=000  0    0
``` to this ```
/dev/hdd5        /media/hdc      vfat    iocharset=utf8,umask=000  0    0
/dev/hdd6        /media/hdd      vfat    iocharset=utf8,umask=000  0    0
``` Remount your partitions: ```
sudo mount -a
```

---

### Post by Geezle on 2006-07-10
> **aysiu said:**
> Make sure these directories exist (if you get an error that they already exist, that's fine): ```
snip
```
Awesome...we're almost there :)  Just one more stumbling block though...I see why you had me make the changes I did, and that's all good, but I noticed one thing that wasn't quite right

```

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2491    20008926    5  Extended
/dev/hdc5               1        2491    20008894+  83  Linux


```

This disk is also a FAT 32 drive, though for some reason here it obviously isn't showing as such.  What gives? :confused:

---

### Post by hinachan on 2006-07-10
> **aysiu said:**
> You need to make a directory where this partition will be accessible (/windows, for example)

Then you need to tell Ubuntu where the location is, the mount point is, and what mount options you want. That's where the editing of the /etc/fstab file comes in.

```
/dev/hda1 /windows vfat iocharset=utf8,umask=000 0 0
```

/dev/hda1 - location
/windows - where to access the location
vfat - filesystem type (FAT32)
iocharset=utf8,umask=000 0 0 - read/write for everyone

OK...so where do you enter all this information?  In shell?  Details, please?  Thanks in advance!  :)

And why isn't there a desktop icon for your hard drive that you can just click to mount, as in other versions of Linux? :(

---

### Post by aysiu on 2006-07-10
> **hinachan said:**
> OK...so where do you enter all this information?  In shell?  Details, please?  Thanks in advance!  :) See my signature.

> 
And why isn't there a desktop icon for your hard drive that you can just click to mount, as in other versions of Linux? :( God knows why. Knoppix has had this functionality for ages.

---

### Post by hinachan on 2006-07-11
> **aysiu said:**
> See my signature.
Wow, useful sig you've got there.  Thanks! :)

> **aysiu said:**
> God knows why. Knoppix has had this functionality for ages.
It's my favorite distro thus far, but it's not recommended to put it on your hard drive.  If only I could, I could DL more of my favorite programs, like the Opera browser...because I really don't like Firefox.  ](*,)

---

### Post by jincast90 on 2006-07-11
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Ah damn, Linux is just hard to understand sometimes, lol.

Anyways, I clicked the link, and had quite a hard time. I used this comman:
sudo fdisk -l 
And found out, my fat32 disk was located at /media/hda4.
So afterwords I type this command: sudo umount /media/hda4
And when Ive done this, it just says this in terminal:
sumount: /media/hda4: not found
So what Am I doing wrong?

---

### Post by Geezle on 2006-07-11
> **Geezle said:**
> Awesome...we're almost there :)  Just one more stumbling block though...I see why you had me make the changes I did, and that's all good, but I noticed one thing that wasn't quite right

```

Disk /dev/hdc: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2491    20008926    5  Extended
/dev/hdc5               1        2491    20008894+  83  Linux


```

This disk is also a FAT 32 drive, though for some reason here it obviously isn't showing as such.  What gives? :confused:
Nobody?  I swear I'm not making this up.  This drive is even showing up with a VFAT partition in my Disks Manager but I can't get access on boot-up.  Should I try mounting it as an Extended/Linux drive instead? :confused:

---

### Post by aysiu on 2006-07-11
> **jincast90 said:**
> Ah damn, Linux is just hard to understand sometimes, lol.

Anyways, I clicked the link, and had quite a hard time. I used this comman:
sudo fdisk -l 
And found out, my fat32 disk was located at /media/hda4.
So afterwords I type this command: sudo umount /media/hda4
And when Ive done this, it just says this in terminal:
sumount: /media/hda4: not found
So what Am I doing wrong? *sudo fdisk -l* will never tell you something is located at /media/hda4. It will tell you it's a /dev--/dev/hda4, for example.

That said, if it's not mounted, then it's not mounted. The ```
sudo umount /dev/hda4
``` command simply makes sure it's not mounted.

> **Geezle said:**
> Nobody?  I swear I'm not making this up.  This drive is even showing up with a VFAT partition in my Disks Manager but I can't get access on boot-up.  Should I try mounting it as an Extended/Linux drive instead? :confused: No idea. We can't know your computer better than you can. I see whatever you've copied and pasted here.

---

### Post by noynac on 2006-07-11
My hard drive is divided into four partitions. They are for windows, ubuntu, the ubuntu swap partition, and a fat32 partition for storage. 

The fdisk -l information is:

/dev/sda1   *           1        3646    29286463+   7  HPFS/NTFS
/dev/sda2            7145       14589    59801962+   5  Extended
/dev/sda3            3647        7144    28097685   83  Linux
/dev/sda5            7145        7296     1220908+  82  Linux swap / Solaris
/dev/sda6            7297       14589    58580991    b  W95 FAT32

Last night, I followed the instructions in this thread to mount the fat32 partition. My fstab file is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/sda6      /media/storage       vfat    iocharset=utf8,umask=000  0    0
/dev/hdc       /media/cdrom0   udf,iso9660 user,noauto     0       0

Everything worked fine, and Nautilus showed the fat32 partition as "storage". However, today, rather than "storage", Nautilus shows the fat32 partion as "_PNG" with a small graphical box under it with the characters 00 1A. 

I undid and redid everything that I had done, but this didn't help. I also deleted and recreated the fat32 partition.

I did find the following thread on this topic, but it didn't offer a solution:

[http://www.ubuntuforums.org/showthread.php?t=184382&highlight=51.9+GB+Volume%3A+Root+Volume](http://www.ubuntuforums.org/showthread.php?t=184382&highlight=51.9+GB+Volume%3A+Root+Volume)

How can I get the correct name of the fat32 partition to show in Nautilus?

Thanks for the help.

---

### Post by aysiu on 2006-07-11
This is an awkward way to solve the problem, but it should work. ```
sudo umount /dev/sda6
sudo rmdir /media/storage
sudo mkdir /storage
sudo nano /etc/fstab
``` Replace this line: ```
/dev/sda6 /media/storage vfat iocharset=utf8,umask=000 0 0
``` with this line: ```
/dev/sda6 /storage vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
ln -s /storage ~/Desktop/storage
```

---

### Post by noynac on 2006-07-11
aysiu,

Thanks for the response. I did as you suggested, and it worked great. :p 

Just out of curiousity, do you know why nautilus displayed the _PNG rather than the storage? It's not all that important, but I can't help but wonder.

Thanks again,

Noynac

---

### Post by aysiu on 2006-07-11
> **noynac said:**
> aysiu,

Thanks for the response. I did as you suggested, and it worked great. :p 

Just out of curiousity, do you know why nautilus displayed the _PNG rather than the storage? It's not all that important, but I can't help but wonder.

Thanks again,

Noynac
No idea, but I think I saw in another thread someone else having that problem.

---

### Post by cjm5229 on 2006-07-11
And why isn't there a desktop icon for your hard drive that you can just click to mount, as in other versions of Linux? :([/quote]

Right click a panel>Add to Panel>System & Hardware> Disk Mounter> Add.

---

### Post by skale on 2006-07-11
It would be much easier to edit the /etc/fstab. 
[http://www.tuxfiles.org/linuxhelp/fstab.html]("http://www.tuxfiles.org/linuxhelp/fstab.html")

---

### Post by noynac on 2006-07-11
<<posting deleted>>

---

### Post by jincast90 on 2006-07-13
> **aysiu said:**
> As far as I know, the default mounting behavior in Ubuntu mounts Windows but in a way that's totally useless--you can't read from or write to the partition. That's what I mean by incorrectly.

In terms of understanding mounting in general--a mounted partition is basically one that's available for use. Where it's mounted is where you can use it. So the partition may exist at /dev/hda1, but you can't just go to /dev/hda1 to access the data there. You have to mount it somewhere else--/media/hda1, for example, or /windows or /music. There has to be some folder you go where you can see the contents of /dev/hda1.

You need to know where you partition exists (/dev/hda1, for example)

You need to make a directory where this partition will be accessible (/windows, for example)

Then you need to tell Ubuntu where the location is, the mount point is, and what mount options you want. That's where the editing of the /etc/fstab file comes in.

```
/dev/hda1 /windows vfat iocharset=utf8,umask=000 0 0
```

/dev/hda1 - location
/windows - where to access the location
vfat - filesystem type (FAT32)
iocharset=utf8,umask=000 0 0 - read/write for everyone

Ok, I am back to try and getting this to work again.
I typed the command which was given. This one:

/dev/hda1 /windows vfat iocharset=utf8,umask=000 0 0

but swapped the hda1 out with hda4. But when I typed this command, and pressed enter. It tells me, that "acces is denied". So whats the problem here?

---

### Post by aysiu on 2006-07-13
That's not a command. It's the line you put in your /etc/fstab

I was trying to explain what all this means in theory.

For the actual commands you type, read this:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

