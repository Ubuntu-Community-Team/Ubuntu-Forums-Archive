---
title: "Relaxing file permissions, size of /home partition"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by Sydney Losstarot on 2006-06-05
I have two questions:

I've heard a separate /home partition is handy.  About how big should this partition be?

I've installed the 5.10 "Breezy Badger" release, and I can't modify/create files except on my desktop.  My hard drive is set up like this:

15GB NTFS (Windows)
9.5GB ext3 (/root)
0.5GB ext3 (/swap)
54GB ext3 (data partition, shared between Windows and ubuntu)

I was referred to a guide ([http://users.bigpond.net.au/hermanzone/p10.html](http://users.bigpond.net.au/hermanzone/p10.html)) in an earlier post of mine, which suggested opening /etc/fstab and changing the "defaults" entry on the lines for each partition I wanted to change with "iocharset=utf8,uname=000".  The guide also said this was only for FAT32 partitions, but I tried it anyway, and ubuntu became unbootable.  But that's beside the point.  How should I go about making it so I can "do things" (i.e. read, write, execute) on any partition I want?

Here's what my /etc/fstab looks like, in case it matters:

------------------------------------

# /etc/fstab: static file system information.
#
# 
<file system> <mount point>   	<type>  	<options>       <dump>  <pass>

proc		/proc           proc    	defaults        0       0

/dev/sda3       /               ext3    	defaults,errors=remount-ro 0       1

/dev/sda5	/media/Archive	ext3		rw,user		0	2

/dev/sda6       none            swap    	sw              0       0

/dev/hda        /media/cdrom0   udf,iso9660 	user,noauto     0       0

/dev/hdb        /media/cdrom1   udf,iso9660 	user,noauto     0       0

/dev/fd0        /media/floppy0  auto    	rw,user,noauto  0       0


-------------------------------------

/dev/sda5, in addition to the root, /dev/sda3, are the two partitions I'd like to be able to use.

---

### Post by Iowan on 2006-06-05
The /home is where most of the user files will be stored - so I'd presume it should be large.
File permissions: I suspect you're running into the need for **sudo**.  I'll let you search around for some information on **sudo** and/or **gksudo**.  In brief, any action requiring root authority (editing most files - other than those in your /home directory) requires **sudo** (eg. **sudo pico mynewfile**.)

---

### Post by Sydney Losstarot on 2006-06-05
Yeah, I've been using sudo.  It seems pretty simple, you just stick it in front of a command that requires root access, right?

So basically, if I want to write to anywhere besides /home/<insert my directory name here>, I'm going to have to use sudo?

---

### Post by Blondie on 2006-06-05
Your /home partition is basically where you're going to store your personal pictures, word processor files, movies, mp3s etc. etc. So it's really your personal needs that determine what it's size should be. Generally my approach is to make my / partition big enough, my swap partition big enough and then the rest goes to the home partition by default.

---

### Post by Sydney Losstarot on 2006-06-05
I think I'm beginning to understand how this works now.  What I really want to do is use that 54GB partition as my data partition for both Windows and ubuntu.  I think I'm going to have ubuntu mount that 54GB partition as my /home directory.  Good idea?

---

### Post by Irony on 2006-06-05
Here are some moving home notes;

[http://www.gentoo.org/doc/en/articles/partitioning-p1.xml](http://www.gentoo.org/doc/en/articles/partitioning-p1.xml)

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[PHP]sudo mkfs.ext3 /dev/hda7
sudo mkdir /mnt/hda7_Home
sudo mount /dev/hda7 /hda7_Home
sudo init 1 (wait, wait... until prompt root@ubuntu:~#)
cd /home
cp -ax * /hda7_Home
cd /
mv /home /home_old
mkdir /home
mount /dev/hda7 /home
init 2  (or Ctrl D)[/PHP]

Now I'm back in graphical mode;

[PHP]sudo gedit /etc/fstab
[/PHP]
Add;

[PHP]/dev/hda7   /home   ext3   defaults   1   2[/PHP]

In short what this does is copy the *contents* of your current home to your new partition (hda7 in my case).

You also make a back-up copy of your current home called home_old which you can later delete. You then add a line to your fstab file to make home mount the hda7 partition as home.

---

### Post by bruenig on 2006-06-05
If you want data sharing, make sure you have gparted installed.
```
sudo apt-get install gparted
```
If you are going to data share on a seperate partition, there is no need for a /home partition for all of the /home data is going to be stored elsewhere anyways. So there really is no point in mounting it on /home unless you want to.  Personally, I would take that 54 GB partition, format as fat32 with Gparted and then mount it. By doing this you don't have to install any drivers or other programs to read or write in windows or linux because they are both able to read and write fat32 by default.

---

### Post by djsroknrol on 2006-06-05
Here's a copy of my Fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdb1       /media/hdb1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hdc1       /media/hdc1	vfat    rw,uid=1000,gid=1003,auto        0       0
/dev/hda3       none            swap    sw	0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto	0       0


```

note the "rw" after vfat...that gives you read/write on the disc of your choice...don't  write to the NTFS volume (there will be problems...:)  )

and DO make that /home....it almost makes the difference between success or failure in Linux...and a smart safeguard if nothing else

---

### Post by kafitz22 on 2006-06-05
[QUOTE=Sydney Losstarot]What I really want to do is use that 54GB partition as my data partition for both Windows and ubuntu.  I think I'm going to have ubuntu mount that 54GB partition as my /home directory.  Good idea?[/QUOTE]

The problem with sharing the home directory will be that you'll have a huge amount of files when you open it in windows that are hidden in linux. The more apps you install, the more excess folders you'll see in windows. (You can see them in Linux with the Ctrl-H command, so I think it be best to share a seperate folder instead. Your choice though.

---

### Post by Ptero-4 on 2006-06-05
Also, IIRC fat32 have a 32GB limit.

---

