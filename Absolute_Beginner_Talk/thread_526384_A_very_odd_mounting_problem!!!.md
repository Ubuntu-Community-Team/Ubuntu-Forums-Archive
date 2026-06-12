---
title: "A very odd mounting problem!!!"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-08-15
Hello,people.Once again I am stuck with a very odd problem.

You see,when running UbuntuLiveCD I noticed that out of four partitions one partition was not mounted.I ignored it thinking that it will auto mount after installation(I even defined a mount point for it).But after installation the problem persist.Its a FAT32 filesystem,so I followed a tutorial in a website(official and unofficial) but no luck.Here is the sample taken from my /etc/fstab from gedit to show you what i mean:


# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    defaults        0       0 
# /dev/sda7 
UUID=050c5cb7-753e-43c2-bfec-46c96fc90509 /               ext3    defaults,errors=remount-ro 0       1 
# /dev/sda1 
UUID=362D-1DF0  /media/DISK_1   vfat    defaults,utf8,umask=007,gid=46 0       1 
# /dev/sda5 
UUID=1C0F-3012  /media/DISK_2   vfat    defaults,utf8,umask=007,gid=46 0       1 
[B][I][U]# /dev/sda6  
UUID=6E3B-CA4B  /media/DISK_3   vfat    defaults,utf8,umask=007,gid=46 0       1 [/U][/I][/B]
# /dev/sda8 
UUID=e3c8638a-7e38-4b54-9f8d-8a475634ccea none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

Yeah its the dev/sda6 which is not auto mounting,and its my personal partition which contains some of my important files(like hard to get songs).So please people help me,a noob:(.

---

### Post by Hospadar on 2007-08-15
can you mount it from the command line?
```
sudo mount /dev/sda6 /media/DISK_3
```

Also can you see the partition in gparted?
(you may need to install it "sudo apt-get install gparted"

---

### Post by Inxsible on 2007-08-15
you do have a folder called DISK_3 under /media, don't you?

---

### Post by Holy Knight on 2007-08-16
> **Inxsible said:**
> you do have a folder called DISK_3 under /media, don't you?

Yeah,I have it.

---

### Post by Inxsible on 2007-08-16
Try and change the way the drive is denoted. Use the device name instead of the UUID.
Change this in the fstab
```
UUID=6E3B-CA4B  /media/DISK_3   vfat    defaults,utf8,umask=007,gid=46 0 1
```to 
```
/dev/sda6 /media/DISK_3 vfat defaults,utf8,umask=007,gid=46 0 1
```

---

### Post by Holy Knight on 2007-08-18
> **Hospadar said:**
> can you mount it from the command line?
```
sudo mount /dev/sda6 /media/DISK_3
```

Also can you see the partition in gparted?
(you may need to install it "sudo apt-get install gparted"

Hi,sorry for the late reply,my internet crashed down.
And no I could not mount the sda6 partition like this.

```
mount: /dev/sda6 already mounted or /media/DISK_3 busy
mount: according to mtab, /dev/sda6 is already mounted on /media/DISK_3

```

and as for gparted,I cannot seem to download it.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gparted is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gparted has no installation candidate

```

---

### Post by Holy Knight on 2007-08-18
> **Inxsible said:**
> Try and change the way the drive is denoted. Use the device name instead of the UUID.
Change this in the fstab
```
UUID=6E3B-CA4B  /media/DISK_3   vfat    defaults,utf8,umask=007,gid=46 0 1
```to 
```
/dev/sda6 /media/DISK_3 vfat defaults,utf8,umask=007,gid=46 0 1
```

No,It didn't work.In boot-up when trying to mount /dev/sda6 it says 

```
 NO FSINFO SECTOR. NOT AUTOMATICALLY CREATING IT.
```

---

### Post by amazingtaters on 2007-08-18
make sure that the UUID in your fstab is the same as the acual UUID of the partition. I repartitioned a drive and my fstab didn't get changed, I had to edit fstab manually so that it would auto mount.

---

### Post by Holy Knight on 2007-08-18
> **amazingtaters said:**
> make sure that the UUID in your fstab is the same as the acual UUID of the partition. I repartitioned a drive and my fstab didn't get changed, I had to edit fstab manually so that it would auto mount.

Yeah I did that.But it was still not auto mounting.

---

### Post by Holy Knight on 2007-08-19
Hello?Anyone?Help?:confused:

---

### Post by Holy Knight on 2007-08-19
please someone help me?:(

---

### Post by orangebase on 2007-08-19
I have read through thoroughly, but [this]("https://answers.launchpad.net/ubuntu/+question/8577") might help or at least give you some insight, if you haven't already seen it. Note the "NO FSINFO SECTOR" problem.

---

### Post by Holy Knight on 2007-08-19
> **orangebase said:**
> I have read through thoroughly, but [this]("https://answers.launchpad.net/ubuntu/+question/8577") might help or at least give you some insight, if you haven't already seen it. Note the "NO FSINFO SECTOR" problem.

Reformat?That was my last option....but then there is no other solution left :(.Coz the other partition is full and the files are like 8.5 GB very big (i have 40 GB harddisk).AWWWWW

---

