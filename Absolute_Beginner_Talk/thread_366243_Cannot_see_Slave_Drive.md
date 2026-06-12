---
title: "Cannot see Slave Drive"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by insyted on 2007-02-20
I have Ubuntu installed on my hard drive as my OS. I hooked up a slave drive to my computer, and set the jumpers for slave.
I went into bios, and set the main drive as the boot drive.
The slave drive has windows installed on it.

My objective is to transfer important files from out of the slave drive, and put them in a folder on my Ubuntu desktop. Then wipe the slave drive.

My problem is that when I go to the places menu, and open up the  "Computer", I only see my main drive and cdrom drive.

I can see the slave drive in BIOS.

---

### Post by bodhi.zazen on 2007-02-20
Mounting and permissions depends on the file system:

_Windows:_ [Psychocats Mount windows ](http://www.psychocats.net/ubuntu/mountwindows)
For read-write: [list=number][*]vfat (FAT) use umask=000
[*]ntfs use [ntfs-3g](http://doc.gwos.org/index.php/NTFS-3g) and a fstab entry something like this:
```
/dev/hda1  /media/windows  ntfs-3g  defaults  0  0
```
[*]An alternate is ntfs-config. ntfs-config uses ntfs-3g to mount windows partitions via a gui :)
[indent][http://doc.gwos.org/index.php/Ntfs-config](http://doc.gwos.org/index.php/Ntfs-config)[/indent][/list]

---

### Post by insyted on 2007-02-20
Hi. Thanks for the insight!
Please tell the steps I need to make in order to make ubuntu recognize the ntfs slave drive.
Do I have to use the terminal?

---

### Post by insyted on 2007-02-20
I ran the Ubuntu Live installation cd, and went to the gdeparted for formatting and partitioning. It did not see the hard drive. Shouldnt that be able to see it if it is fupposed to format it?

---

### Post by bodhi.zazen on 2007-02-20
Can you open a terminal and post the output of :

```
sudo fdisk -l
```

---

### Post by insyted on 2007-02-20
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60054   482383723+  83  Linux
/dev/sda2           60055       60801     6000277+   5  Extended
/dev/sda5           60055       60801     6000246   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24321   195358401    7  HPFS/NTFS
user1@tyrelia:~$

---

### Post by kelbizzle on 2007-02-20
> **insyted said:**
> I have Ubuntu installed on my hard drive as my OS. I hooked up a slave drive to my computer, and set the jumpers for slave.
I went into bios, and set the main drive as the boot drive.
The slave drive has windows installed on it.

My objective is to transfer important files from out of the slave drive, and put them in a folder on my Ubuntu desktop. Then wipe the slave drive.

My problem is that when I go to the places menu, and open up the  "Computer", I only see my main drive and cdrom drive.

I can see the slave drive in BIOS.

If you already connected the drive as a slave this will help you back up the stuff you want on here. Follow them step by step and you'll be fine in no time.

If your looking to mount your slaved hard drive thats located at /dev/sdb1 and mount it at /media/windows type into terminal:
```
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
that will mount it manually.

If you want to unmount the drive
```
sudo umount /media/windows
```

If you want to mount it on boot...type. You have to edit your fstab. 
```
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab

```
 Add this line..
```
/dev/sdb1    /media/windows ntfs  nls=utf8,umask=0222 0    0

```
then remount the fstab manually with this command
```
sudo mount -a
```

You should have read only access to your files on that partition located at /media/windows



**[COLOR="Red"]Edit:[/COLOR]**changed to hdb1 to sdb1

---

### Post by insyted on 2007-02-20
> **kelbizzle said:**
> If you already connected the drive as a slave this will help you back up the stuff you want on here. Follow them step by step and you'll be fine in no time.

If your looking to mount your slaved hard drive thats located at /dev/hdb1 and mount it at /media/windows type into terminal:
```
sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

```
that will mount it manually.
Before I go over the rest of your post, please explain what this means.
I don't understand any thing you are saying. 
Do I have to enter that code into the terminal?

---

### Post by insyted on 2007-02-20
OK. I enetered that code.

user1@tyrelia:~$ sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: mount point /media/windows/ does not exist
user1@tyrelia:~$ 


Now how do I access the drive from the "Computer" places?

---

### Post by kelbizzle on 2007-02-20
Ooops I'm sorry you have to make the folder first type this to do it

```
sudo mkdir /media/windows
```

---

### Post by kelbizzle on 2007-02-20
After you make the directory to mount the drive you can issue the mount command. I'm sorry again for the left out step.

---

### Post by bodhi.zazen on 2007-02-20
> **insyted said:**
> OK. I enetered that code.

user1@tyrelia:~$ sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
mount: mount point /media/windows/ does not exist
user1@tyrelia:~$ 


Now how do I access the drive from the "Computer" places?

First, thanks kelbizzle for the detailed post :p

insyted : All you need to do is make a mount point :
```
sudo mkdir /media/windows
sudo mount /dev/sdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

Use the up arrow keys so you do not need to re-type commands ;)

---

### Post by insyted on 2007-02-20
It worked : )!
Thanks!!

---

