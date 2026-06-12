---
title: "[SOLVED] New Partition Read Only"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Brian Dempster on 2007-12-06
I just made a new partition and now it is read only. I do not have permission to change permissions.

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb3: 11/5537792 files (9.1% non-contiguous), 218840/11056736 blocks

How can I get permission to change permissions?

---

### Post by SpacePilot on 2007-12-06
You have permition to do anything if you are root. Type sudo su -

You can also set permitions for a partition in your /etc/fstab

---

### Post by hyper_ch on 2007-12-06
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Brian Dempster on 2007-12-06
>You have permition to do anything if you are root. Type sudo su -

>You can also set permitions for a partition in your /etc/fstab

I must not understand what happens when I us the sudo su -
I tried this and it seems I am still not logged in as root.

What would I change in this file? I am trying to get access to sdb3

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c7f5b6fb-4263-48a3-a1a4-1a8354550830 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=090f9d11-e230-4093-92f9-33a8a202300e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Brian Dempster on 2007-12-06
I am sorry but I am so new to ubuntu that I don't see anything in [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
that would help me.
Could you point me a little closer to what I would need to do?

---

### Post by forestpixie on 2007-12-06
I think that was aimed more at making you aware of the dangers of using root

as faar as your new partition goes, assuming that it's an ext3 partition - you need to get it to mount at start up - have a look at this page - where it shows > sudo mount /dev/hdd1 /media/mynewdrive you'll need to change the hdd1 to suit your new partition 

you should be able to get that information by using fdisk

```
sudo fdisk -l
```
have a look at that see if it helps

Edit - it would help I guess if I put the page on the post :)

[https://help.ubuntu.com/community/InstallingANewHardDrive#head-4cf3116dcfc30495ffcb3500c37659c8e7ec301b](https://help.ubuntu.com/community/InstallingANewHardDrive#head-4cf3116dcfc30495ffcb3500c37659c8e7ec301b)

---

### Post by Brian Dempster on 2007-12-06
I think I am beginning to understand what is happening.
So far I have only created a new directory on my filesystem called media\mynewdrive

How can I log onto the new partition. I have tried:

root@Dempster-desktop:~# sudo su -
root@Dempster-desktop:~# /dev/sdb3
-su: /dev/sdb3: Permission denied
root@Dempster-desktop:~# 

I think if I could log onto sdb3 I could then handle the balance. I Think???

---

### Post by iris-n on 2007-12-06
I wouldn't use sudo -su in vain like this.
Just put sudo before each critical command, it's better to learn which parts of the system are dangerous to mess with and which aren't.

That's the whole output of the cat?
I can't see your sdb3 there.

For myself I changed the options to defaults =).

But please, cat again and paste here.

---

### Post by Brian Dempster on 2007-12-06
Working in the Root Terminal, there must be a way to change from one drive to another.
I need to make a directory on my new partition but I can't seem to change to the new partition. dev/sdb3

If in dos if I were c drive and wanted to change to d drive all I would do is type d: and hit enter.

I am sure there must be a way but I just can not find it. I am getting very good help in everything I need to do after I get this directory made. as in mkdir /media/mynewdrive
and then give access to my family to share this drive.

---

### Post by PmDematagoda on 2007-12-06
I do not think that you can access any partition that is not mounted.

To access /dev/sdb3, do this:-

1) Open Nautilus in root mode using:-
```

gksudo nautilus
```

2) Then go to the /media directory and make a folder with whatever name you want.

3) Close Nautilus, then do:-

```
sudo mount /dev/sd3 /media/nameofnewfolder
```

That should do the trick.

---

### Post by shadow-of-sin on 2007-12-06
Type this in the terminal:
```
cd /media/sdb3
```

---

### Post by Brian Dempster on 2007-12-06
I have not yet been able to switch to sdb3 to make the media directory, but I tried and this is what I get.

root@Dempster-desktop:/home/brian# cd /media/sdb3
bash: cd: /media/sdb3: No such file or directory
root@Dempster-desktop:/home/brian#

---

### Post by taurus on 2007-12-06
So you want to mount /dev/sdb3 so you can access it.  What filesystem is /dev/sdb3?  Post the output of this command here.

```
fdisk -l <-- lower case letter l, not number 1
```

---

### Post by Brian Dempster on 2007-12-06
>gksudo nautilus
It looks like this is allowing me to make folders in root. The new partition is still not showing up.

---

### Post by Brian Dempster on 2007-12-06
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18530   148842193+   7  HPFS/NTFS
/dev/sda2           18531       19457     7446127+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3b9d6b02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8924    71681998+  83  Linux
/dev/sdb2           14431       14593     1309297+   5  Extended
/dev/sdb3            8925       14430    44226945   83  Linux
/dev/sdb5           14431       14593     1309266   82  Linux swap / Solaris

Partition table entries are not in disk order
root@Dempster-desktop:/home/brian# 

formated ext3

---

### Post by Brian Dempster on 2007-12-06
I can now cd to the directory. The only thing now is to get it to mount at boot. I thought I had that working but it seems that I have to enter my password and mount it. I will try this on my own for now with info from another thread.

Thank You for your help.

---

### Post by PmDematagoda on 2007-12-06
Sorry, I made a typo, the command is:-

```
sudo mount /dev/sdb3 /media/nameofnewfolder
```

---

### Post by Brian Dempster on 2007-12-06
With your help I now have a disk that I can share with my family. I am still working on getting it to mount with each boot.

In what file do I add the lines below so that my family will have permisions?

or in a more flexible way, practical if you have several users, allow for instance the users in the plugdev group (usually those who are meant to be able to mount removable disks, desktop users) to create files and sub-directories on the disk:

    *

        sudo chgrp plugdev /media/mynewdrive
        sudo chmod g+w /media/mynewdrive
        sudo chmod +t /media/mynewdrive
        

The last "chmod +t" adds the sticky bit, so that people can only delete their own files and sub-directories in a directory, even if they have write permissions to it (see man chmod).

---

### Post by PmDematagoda on 2007-12-06
If you want the partition mounted at boot, do this:-

1) Open up fstab for editing using:-

```
sudo gedit /etc/fstab
```

2) Then add the following line:-

```
/dev/sdb3 /media/nameoffolder fs defaults

```
fs stands for the file system, if it ext3, then type ext3, if JFS, then jfs.

3) Save the file.

That's it.

---

### Post by Brian Dempster on 2007-12-06
With all the help I now can mount and work with this new partition.
Still working on getting it to mount at boot but I think I will dig through some of the other threads for this.
 I will try and close this thread. My thanks to you all. :)

---

### Post by PmDematagoda on 2007-12-06
You are welcome:).

But I already gave you the answer to mount the partition at boot, why don't you try that?

---

### Post by Brian Dempster on 2007-12-06
I tried that and so far it is not mounting.
Is the following correct?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=c7f5b6fb-4263-48a3-a1a4-1a8354550830 /               ext3    defaults,errors=remount-ro 0       1
# [COLOR="Blue"]/dev/sdb3    /media/disk ext3	0	0[/COLOR]
UUID=090f9d11-e230-4093-92f9-33a8a202300e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by PmDematagoda on 2007-12-06
Uhhh, I do not think the entry has to commented, don't you?;)

The entry has to be:-

```
/dev/sdb3 /media/disk ext3 0 0
```

Without a # infront of it. Or you will have to provide a specific ID for it, about which I have no idea.

---

### Post by taurus on 2007-12-06
If you want to mount /dev/sdb3 at boot, just add an entry in /etc/fstab for it.  Edit /etc/fstab with

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb3   /media/sdb3   ext3   defaults   0   1
```
Save it and then reboot.

---

### Post by Brian Dempster on 2007-12-06
I just tried this and was once again locked out of the partition. I did not have permission.
So I have put it back for the night. I will have to work this issue Friday.
Thanks

---

### Post by PmDematagoda on 2007-12-06
I'm really sorry, I forgot one part of the code, it should look like this:-

```
/dev/sdb3 /media/disk ext3 defaults 0 2
```

---

### Post by Brian Dempster on 2007-12-07
When I added this line the partition did not even show up in Places-Computer.
/dev/sdb3   /media/sdb3   ext3   defaults   0   1

I then changed it to:
/dev/sdb3   /media/disk   ext3   defaults   0   1
thinking maybe there had been I typo but It still it was not in Places-Computer.

I then removed the line and I am back where I can load it manually.

I will have to work on this Friday night.
Thanks for your help tonight.

---

