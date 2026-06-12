---
title: "I installed  ntfs-3g but I still cant write to NTFS drives"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by videocheez on 2007-06-22
I installed  ntfs-3g but I still can't write to NTFS drives.  Is there anything else to do to make this work?

Thx,

VC

---

### Post by wormser on 2007-06-22
Did you go to Applications> System Tools> NTFS Configuration Tool?

Is the drive mounted?

---

### Post by videocheez on 2007-06-22
No.  I don't even see the program there.  Maybe my installation method was no good.  I installed by: typing sudo apt-get install ntfs-3g-* and I did not reboot if that matters.

---

### Post by wormser on 2007-06-22
You might want to try a reboot.  But first right click on applications and Edit Menus.  Take a look for it there and add put a check mark to make it visible.  It won't hurt to install it again.

```
sudo apt-get install ntfs-3g
```

It will let you know if it is installed.  The - at the end of your install concerns me.

---

### Post by bvanaerde on 2007-06-22
You forgot a package... it's called ntfs-config if I remember it well.
edit: [more info can be found in this thread]("http://ubuntuforums.org/showthread.php?t=337970").

---

### Post by videocheez on 2007-06-22
Ok.  Nice trick about right clicking on applications but I did not see it there.  I did retyped you code from the terminal and read teh following message:

don@don-ubuntu:~$ sudo apt-get install ntfs-3g
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


I suppose I ought to reboot even though I didn't linux needed reboots except for video driver modifications.

---

### Post by bvanaerde on 2007-06-22
You don't need to reboot at all.
Just run:
> sudo apt-get install ntfs-config
I see you're running Ubuntu 7.04 so this package should be in the repositories.

---

### Post by polopolo on 2007-06-22
And if it not work, and if you installed ntfs-config, and it's not working from the menu, then open you're console and type

```
sudo ntfs-config
```

---

### Post by videocheez on 2007-06-22
> **bvanaerde said:**
> You don't need to reboot at all.
Just run:

I see you're running Ubuntu 7.04 so this package should be in the repositories.


This is what I got.  What do you think?

don@don-ubuntu:~$ sudo apt-get install ntfs-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config


Thx,

VC

---

### Post by Inxsible on 2007-06-22
Applications -- > Add/Remove

Search for ntfs and install NTFS Configuration Tool.

Then Applications -- > System Tools -- > NTFS Configuration Tool. Enable write support for Internal and External drives. 

If you cannot write after that, its probably an ownership or permissions issue.

---

### Post by videocheez on 2007-06-22
> **Inxsible said:**
> Applications -- > Add/Remove

Search for ntfs and install NTFS Configuration Tool.

Then Applications -- > System Tools -- > NTFS Configuration Tool. Enable write support for Internal and External drives. 

If you cannot write after that, its probably an ownership or permissions issue.

Okay,

i was able to find the program this way by selecting all open source instead of the default of Ubuntu supported applications. 

Thx for the tip,

VC

---

### Post by videocheez on 2007-06-22
Hey.  I  just installed the program and a Windows NTFS drive that I had could previously mount but had read-only privileges is now unmountable.:(  Read-only is better than unmountable.  Now I cant find any buttons to reverse it and make this drive mountable again.

VC

---

### Post by Brightbelt on 2007-06-22
Hi,
I would try a restart for one. I've found that a lot of newly installed programs won't get settled into the menus correctly until I do a restart. Call me a retard if you will, but I've noticed it. ;)

Then I would check the Applications Menu/System Tools/NTFS Configuration Tool once again after your restart  just to make sure something  isn't Unchecked. 

Also, you can always go back to Add/Remove and Un-install what you just did by Unchecking the box etc if nothing else gets your mount back on your drive. 

If none of this works, I would try Uninstalling ntfs-3g and reinstalling it.

I hope this helps,....Frank B.

---

### Post by videocheez on 2007-06-23
Ok.  I'll try it again because now after a reboot, the drive doesn't even show up in my computer.

---

### Post by Inxsible on 2007-06-23
Post the output of the following commands.

```
sudo fdisk -l
``` -l is lowercase L not 1.

```
gksudo gedit /etc/fstab
```

Also, is this drive an external drive?

---

### Post by videocheez on 2007-06-23
> **Inxsible said:**
> Post the output of the following commands.

```
sudo fdisk -l
``` -l is lowercase L not 1.

```
gksudo gedit /etc/fstab
```

Also, is this drive an external drive?

The drive that I seemed to lost is in internal SATA drive. 

My Hardrives:
[LIST=1]
[*]Linux Drive eSATA 74GB Raptor
[*]Windows Drive (2 x 74GB Raptor) RAID 0..I have never been able to mount this drive
[*]Windows Storage Drive 250GB Samsung SATA...this is the drive that I can no longer see after running NTFS config.
[*]Media Drives 4 x 300 GB USB External all NTFS except for one is FAT32.  I have always been able to mount these drives
[/LIST]

don@don-ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18079   145219536    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1049        1049           0   14  Hidden FAT16 <32M
Partition 1 does not end on cylinder boundary.
/dev/sdb2            2085        4178    16809999+   0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3            2220        2220           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1          86      688768   1f  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8666    69609613+  83  Linux
/dev/sdc2            8667        9039     2996122+   5  Extended
/dev/sdc5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdf: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       36482   293041633+   7  HPFS/NTFS

Disk /dev/sdg: 250.9 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdh: 300.0 GB, 300068372480 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       36481   293033601    7  HPFS/NTFS



Here are the results of the second command:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=0c3037a2-dce5-4854-b4a1-765240a63fef / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=5e42b980-06e5-443f-acd0-f6bf8e17b852 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sdd1 /media/storage_drv ntfs-3g defaults,locale=en_US.UTF-8 0 0

Thanks for taking a look and what does all of this stuff mean.  It's kina hard for me to interpret.

VC

---

### Post by Inxsible on 2007-06-23
1) your Linux drive is /dev/sdc which mounts correctly sdc1 = / and sdc5 = swap

2) sda1 and sdb1 is your Windows RAID 0 drive. sda1 has a Windows installation. There are some errors on your sdb. You might want to re-format it.

3)sdd is 250GB, NTFS formatted, and its mounted @ /media/storage_drv

4) sde is 250GB each, FAT32 formatted but not mounted.

5) sdf is 300 GB and NTFS formatted...but i dont see it mounted

6) sdg is 250 GB NTFS formatted but not mounted. This drive also has a Windows installation on it.

7) sdh is 300 GB NTFS formatted but not mounted

Wow thats a lot of HDD space !!!

---

### Post by Inxsible on 2007-06-23
To mount these drives, add the following lines to your fstab.
you can open fstab in edit mode as follows :

```
gksudo gedit /etc/fstab
``` Then add 

```
/dev/sda1 /media/mySDA ntfs-3g defaults,locale=en_US.UTF-8 0 0

/dev/sde1 /media/mySDE vfat defaults,locale=en_US.UTF-8 0 0

/dev/sdf1 /media/mySDF ntfs-3g defaults,locale=en_US.UTF-8 0 0

/dev/sdg1 /media/mySDG ntfs-3g defaults,locale=en_US.UTF-8 0 0

/dev/sdh1 /media/mySDH ntfs-3g defaults,locale=en_US.UTF-8 0 0
``` you can change the names of the mount points from mySD* to anything you want or that makes sense to you. You can also mount it somewhere else instead of under /media. But it would be better if you kept all together. If there are some drives that you do NOT want to access from Linux, then do not put the entry for that drive in fstab.


NOTE: You can do the same for sdb1. This is assuming that you will format sdb to NTFS too since its currently unformatted and does not have a filesystem. If you format it to something else, the entries in fstab will change. If you format it to FAT32 then use the line similar to sde.

After you add the above lines

```
sudo mount -a
```

Hope thats clear enough

---

### Post by videocheez on 2007-06-23
> **Inxsible said:**
> 1) your Linux drive is /dev/sdc which mounts correctly sdc1 = / and sdc5 = swap

2) sda1 and sdb1 is your Windows RAID 0 drive. sda1 has a Windows installation. There are some errors on your sdb. You might want to re-format it.

3)sdd is 250GB, NTFS formatted, and its mounted @ /media/storage_drv

4) sde is 250GB each, FAT32 formatted but not mounted.

5) sdf is 300 GB and NTFS formatted...but i dont see it mounted

6) sdg is 250 GB NTFS formatted but not mounted. This drive also has a Windows installation on it.

7) sdh is 300 GB NTFS formatted but not mounted

Wow thats a lot of HDD space !!!

Okay.  I guess I don't exactly know what mounting means so I'm not sure what i want to do.  I do not want linux tobe able to mount  the Windows RAID drives.  One of my drives does not show up in places>computer.  This drive had the name storage drive.  You say that it is mounted yet I cannot see it any moe since I saw it messed everything up with NTFS-config.  What I want to accomplish is to beable to read and write to any of the computers drives accept for the RAID 0 drives.  Also, how can you tell that one of the windows raid drives has errors?

---

### Post by Inxsible on 2007-06-23
> **videocheez said:**
> Okay.  I guess I don't exactly know what mounting means so I'm not sure what i want to do.  I do not want linux tobe able to mount  the Windows RAID drives.  One of my drives does not show up in places>computer.  This drive had the name storage drive.  You say that it is mounted yet I cannot see it any moe since I saw it messed everything up with NTFS-config.  What I want to accomplish is to beable to read and write to any of the computers drives accept for the RAID 0 drives.

In that case do not add the lines for sda and sdb. Add the rest of the lines in fstab and you should then be able to read and write to those drives.

if your sdd or storage_drv is not accessible, try this

```
sudo umount /dev/sdd1

sudo mount -t ntfs-3g /dev/sdd1 /media/storage_drv -o iocharset=utf8,umask=000
```

---

### Post by Inxsible on 2007-06-23
> **videocheez said:**
> Okay.  I guess I don't exactly know what mounting means so I'm not sure what i want to do.  I do not want linux tobe able to mount  the Windows RAID drives.  One of my drives does not show up in places>computer.  This drive had the name storage drive.  You say that it is mounted yet I cannot see it any moe since I saw it messed everything up with NTFS-config.  What I want to accomplish is to beable to read and write to any of the computers drives accept for the RAID 0 drives.  Also, how can you tell that one of the windows raid drives has errors?

Do you mean that the icon doesnt come up on desktop ? Have you tried navigating to the /media/storage_drv to see if you can actually read/write in to it ?

---

### Post by videocheez on 2007-06-23
Nice!:D  That worked.  Thanks for babying me along.  
I suppose I wouldn't have lost access to that drive if I wasn't using that ntfs-config graphical utility.  Your suggested command worked great and I was finally able to write to that drive.

I would like to use the same drives names as I have in windows when I mount in Linux so I know which drive it is or at least I want to have a name that references linux and windows for example I might call it storage_drv_sdd1.  The storage_drv part is from Windows and the sdd1 is from Linux.

Anyways should I add a command to my fstab for this drive.  I didn't see the command for this drive in your previous post a few back.  Would the following code work for adding this drive to fstab?
```

/dev/sdd1 /media/storage_drv ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

or could I use this one instead?

```

/dev/sdd1 /media/storage_drv_sdd1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

```


thx,

VC

---

### Post by Inxsible on 2007-06-23
> **videocheez said:**
> Nice!:D  That worked.  Thanks for babying me along.  
I suppose I wouldn't have lost access to that drive if I wasn't using that ntfs-config graphical utility.  Your suggested command worked great and I was finally able to write to that drive.

I would like to use the same drives names as I have in windows when I mount in Linux so I know which drive it is or at least I want to have a name that references linux and windows for example I might call it storage_drv_sdd1.  The storage_drv part is from Windows and the sdd1 is from Linux.

Anyways should I add a command to my fstab for this drive.  I didn't see the command for this drive in your previous post a few back.  Would the following code work for adding this drive to fstab?
```

/dev/sdd1 /media/storage_drv ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

or could I use this one instead?

```

/dev/sdd1 /media/storage_drv_sdd1 ntfs-3g defaults,locale=en_US.UTF-8 0 0

```


thx,

VC

I didnt have it because it was already in your fstab. The first one you listed is exactly how it is in fstab. Is it not ?

Do not change the mount point now since its already working at storage_drv. if you want to create a new mount point called storage_drv_sdd1 you will first have to create that folder and then make sure you have permissions on it.

Did you NOT want to mount all your other drives ? the sde sdf sdg and sdh ?

---

### Post by videocheez on 2007-06-23
> **Inxsible said:**
> 
Did you NOT want to mount all your other drives ? the sde sdf sdg and sdh ?
Yes, I do want to mount the other drives and I want to put them in media too but I don't want to call them mySDE or mySDF.  I want to call them with the names that they are mapped in windows for example Drive_L in windows is sdg1 in Linux.  
Unfortunately, I can't tell which drive one of the Windows drives is sdf1 or sdh1.  If I could tell how full they are then I would know which one is Drive_M and which one Drive_O.  Tomorrow I will turn off one of them and run
```

sudo fdisk -l

``` 
and see if sdh1 or sdf1 is still on the list.  Of course if you know a command that would tell me how full the drives are with respect to the their linux names, then I might not have to try my turning off the drive experiment.  It's getting late or I should ssay it's getting early so I will continue with this tomorrow.

Thx for your help so far,

VC

---

### Post by videocheez on 2007-06-23
Back to work:

Here is a current copy of my fstab:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=0c3037a2-dce5-4854-b4a1-765240a63fef / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=5e42b980-06e5-443f-acd0-f6bf8e17b852 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sdd1 /media/storage_drv ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdg1 /media/DRIVE_L ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdf1 /media/DRIVE_M ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdh1 /media/DRIVE_O ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sde1 /media/HD-HCU2 vfat defaults,locale=en_US.UTF-8 0 0

I can't see write to DRIVE_M or DRIVE_O mounted in media and I cant seem to mount DRIVE_L
This is the error that I received:
don@don-ubuntu:~$ sudo umount /dev/sdg1
umount: /dev/sdg1: not mounted
don@don-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdg1 /media/DRIVE_L -o iocharset=utf8,umask=000
fusermount: failed to access mountpoint /media/DRIVE_L: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdg1 (DRIVE_L)

Any more help will be appreciated,

VC

---

### Post by Inxsible on 2007-06-23
> **videocheez said:**
> Back to work:

Here is a current copy of my fstab:

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdc1 :
UUID=0c3037a2-dce5-4854-b4a1-765240a63fef / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdc5 :
UUID=5e42b980-06e5-443f-acd0-f6bf8e17b852 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sdd1 /media/storage_drv ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdg1 /media/DRIVE_L ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdf1 /media/DRIVE_M ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdh1 /media/DRIVE_O ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sde1 /media/HD-HCU2 vfat defaults,locale=en_US.UTF-8 0 0

I can't see write to DRIVE_M or DRIVE_O mounted in media and I cant seem to mount DRIVE_L
This is the error that I received:
don@don-ubuntu:~$ sudo umount /dev/sdg1
umount: /dev/sdg1: not mounted
don@don-ubuntu:~$ sudo mount -t ntfs-3g /dev/sdg1 /media/DRIVE_L -o iocharset=utf8,umask=000
fusermount: failed to access mountpoint /media/DRIVE_L: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sdg1 (DRIVE_L)

Any more help will be appreciated,

VC

Thats because you havent created the folders called Drive_L under /media. Remember Linux is case sensitive. So DRIVE_L and Drive_L are two completely different folders as fas as Linux is concerned.

---

### Post by Inxsible on 2007-06-23
If you havent already done so, you can create the folders by using the following command

```
sudo mkdir /media/DRIVE_L
``` Make sure you have the folders for all your drives. DRIVE_M DRIVE_O and HD-HCU2

---

### Post by videocheez on 2007-06-23
> **Inxsible said:**
> If you havent already done so, you can create the folders by using the following command

```
sudo mkdir /media/DRIVE_L
``` Make sure you have the folders for all your drives. DRIVE_M DRIVE_O and HD-HCU2

Yes.  I can see the folders in side of those drives but I cannot write to the two NTFS drives DRIVE_M & DRIVE_O yet.  Do you think I follow the following sequence of code i will be able to write to DRIVE_O for example?  Funny thing, BTW the NTFS drive that I cannot write to appear on my desk top and the have been their  since I installed Ubuntu.  After I have executed the code that you have suggested those drives no longer appear on my desktop and only appear in  /media.  I guess it's not funny I just don't understand what's going on.

```

sudo umount /dev/sdh1

sudo mount -t ntfs-3g /dev/sdh1 /media/DRIVE_O -o iocharset=utf8,umask=000

sudo mkdir /media/DRIVE_O

sudo mount -a

```

---

### Post by Inxsible on 2007-06-23
If you cannot write to the drives, its probably a permissions issue.

you can change the ownership by

```
sudo chown -R <your username>:<your group> <device mount point>
```

so assuming that your username is videocheez

```
sudo chown -R videocheez:videocheez /media/DRIVE_M
```

```
sudo chown -R videocheez:videocheez /media/DRIVE_O
```

---

### Post by quincy_the_penguin on 2007-06-23
Run "sudo gedit /etc/fstab" in a terminal.  In the text editor that pops up, look for the word "ntfs" and replace it with "ntfs-3g".  Save, then restart your computer.

---

### Post by videocheez on 2007-06-23
> **Inxsible said:**
> If you cannot write to the drives, its probably a permissions issue.

you can change the ownership by

```
sudo chown -R <your username>:<your group> <device mount point>
```

so assuming that your username is videocheez

```
sudo chown -R videocheez:videocheez /media/DRIVE_M
```

```
sudo chown -R videocheez:videocheez /media/DRIVE_O
```

Didn't appear to be a permission issue.  I just did what you suggested earlier and now I'm able to write to those drives but your previous response generated a couple of more questions.

[LIST=1]
[*]are user name and group the same?
[*]how can i make my drives appear on Places.
[/LIST]

When I first installed Ubuntu all of my drives appeared in Places.  Now only DRIVE_M, DRIVE_O and HD-HCU2 appear in Places.

I would like to either make all the drives appear in Places or none of the appear their.  I just like to be consistent.

Thx,

VC

---

### Post by videocheez on 2007-06-23
Hey if you got a sec something kinda strange has happened.  For example DRIVE_O has nothing in it but a DRIVE_O_ was created and thats where all of my files are.  This was noticed after rebootng.  The same thing applies for DRIVE_M and DRIVE_L.  Please see the following file information and notice that the drives letter have changed.  For example, former sde1 is now sdi1.  WTF?

don@don-ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18079   145219536    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            1049        1049           0   14  Hidden FAT16 <32M
Partition 1 does not end on cylinder boundary.
/dev/sdb2            2085        4178    16809999+   0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3            2220        2220           0    0  Empty
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1          86      688768   1f  Unknown
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdc: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        8666    69609613+  83  Linux
/dev/sdc2            8667        9039     2996122+   5  Extended
/dev/sdc5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdi: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1       30401   244196001    c  W95 FAT32 (LBA)

Disk /dev/sdj: 300.0 GB, 300068372480 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdk: 250.9 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1   *           1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdl: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1       36482   293041633+   7  HPFS/NTFS


Any help will be appreciated,

VC

---

### Post by videocheez on 2007-06-24
Could you help me out a little bit more.  I learned a lot last night and I don't think I'm gonna find as useful information so quickly as you provided me last night.  
My NTFS USB drives changed letters after reboot and I want to know why or if you have an idea.  All of the work that we did making the drives so that i could write to them went out the window after the reboot.  I could go through the exercise and modify my fstab file to fit the new drive letters but I figure that they may change again so what's the use.  

Thx in advance,

VC

---

### Post by BlacKsheep88 on 2007-09-10
I've installed both ntfs-3g and ntfs-config, both my NTFS drives are mounted, but I can't establish write permissions to them. When I open up ntfs-config, the area that allows me to select write permissions to internal drives is greyed out. Is this a known issue?

---

