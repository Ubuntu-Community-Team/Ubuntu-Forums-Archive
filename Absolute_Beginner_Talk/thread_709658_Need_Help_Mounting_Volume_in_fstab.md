---
title: "Need Help Mounting Volume in fstab"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by tootlet on 2008-02-27
Greetings,
I have a computer set up booting XP, Vista and Ubuntu. I have XP and Vista on (using Ubuntu nomenclature) what would be sda and Ubuntu on sdb. I have sda partitioned into sda1 for XP in NTFS, Vista in sda2 with NTFS and sda3 with ext3. I put a driver into the Windows OS's so they can read and write to sda3. In Ubuntu I can mount the "volume" I'm calling sda3 but in read only mode as it is the property of root. I want to set up an fstab entry that mounts this volume with rw privileges for me but I don't know how to do this. Actually, I just want to be able to read and write to this partition on the first hard drive without having to go through many steps every time I want to use it. I think fstab is where I need to be. But I don't really understand what it should read. 

/dev/sda3 /mnt/data ext3, rw o o

Something like this? When I mount it by going to places, computer and right clicking on the volume it doesn't show properties or label it sda3. So I really don't know what I'm doing. Pointers would be appreciated. 

Thank you.
Tom

---

### Post by LuisGMarine on 2008-02-27
Sorry I'm having a hard time decripting what you wrote.  First run some commands to help us better understand your situation.

paste the output your fstab:

```
cat /etc/fstab
```

or

```
sudo gedit /etc/fstab
```

then run this command and paste the outputs:

```
sudo fdisk -l
```

Seems like you are having a bad time with getting the permissions to be set to the user.  That's an easy fix, but I want to make sure it is the right thing before I tell you to do it.

---

### Post by tootlet on 2008-02-28
Thanks for the help. I'm sure clarification is needed as I do have a hard time articulating my problem,

Here's the result of cat etc:
tootlet@Oliphant:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=880e4931-f6bb-4094-8a77-bbf832ee7474 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=78428c3b-2e62-44d0-ac78-e6dc22b3e2dd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

This (obviously) does not show the hard drive that has the 3 partitions, 1 for XP, 1 for Vista and 1 ext3 for data.

Here's fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x951f6ded

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3222    25880683+   7  HPFS/NTFS
/dev/sda2            3223        9636    51520455    7  HPFS/NTFS
/dev/sda3            9637       30401   166794862+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079954

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris

What I want to do is have /dev/sda3 mounted in fstab with rw privileges to tootlet when I boot up Ubuntu. I'm only going to rarely use Windows though I need them for a couple of programs for work. But I'm don't want to leave all that beautiful storage without accessing it with Ubuntu. 

Thanks for any help.

Tom

---

### Post by Voland on 2008-02-28
Try to install ntfs-config and mount your partitions.

---

### Post by jw5801 on 2008-02-28
> **tootlet said:**
> Greetings,
I have a computer set up booting XP, Vista and Ubuntu. I have XP and Vista on (using Ubuntu nomenclature) what would be sda and Ubuntu on sdb. I have sda partitioned into sda1 for XP in NTFS, Vista in sda2 with NTFS and sda3 with ext3. I put a driver into the Windows OS's so they can read and write to sda3. In Ubuntu I can mount the "volume" I'm calling sda3 but in read only mode as it is the property of root. I want to set up an fstab entry that mounts this volume with rw privileges for me but I don't know how to do this. Actually, I just want to be able to read and write to this partition on the first hard drive without having to go through many steps every time I want to use it. I think fstab is where I need to be. But I don't really understand what it should read. 

/dev/sda3 /mnt/data ext3, rw o o

Something like this? When I mount it by going to places, computer and right clicking on the volume it doesn't show properties or label it sda3. So I really don't know what I'm doing. Pointers would be appreciated. 

Thank you.
Tom

Yep, your line is correct except without the comma after ext3. You could also make the last field 2 instead of 0. That last field determines whether fsck should check the filesystem at startup, the root partition (/) should have a value of 1, and other partitions you want to check should have a value of 2.

---

### Post by karthikbalaji on 2008-02-28
Install ntfs-3g . The ntfs-3g driver is an open source, GPL licensed, third generation Linux
NTFS driver which was implemented by the Linux-NTFS project. It provides
full read-write access to NTFS, excluding access to encrypted files, writing
compressed files, changing file ownership, access right.

ntfs-3g is based on FUSE  ...

apt-get install ntfs-3g 

I guess it ll automatically detect and mount the ntfs volumes. However u can always mount it manually or add it to fstab after installing ntfs-3g

---

### Post by sisco311 on 2008-02-28
0.) if you have gusty (7.10) you don't need the ntfs-3g driver

1.) create mount points:
```
sudo mkdir /media/xp
sudo mkdir /media/vista
sudo mkdir /media/ext3
```2.) edit your fstab:
```
gksu gedit /etc/fstab
```add this lines:
> /dev/sda1 /media/xp ntfs defaults,umask=007,gid=46 0 1
/dev/sda2 /media/vista ntfs defaults,umask=007,gid=46 0 1
/dev/sda3 /media/ext3 ext3    defaults        0       23.) to get write permission on the ext3 volume chown the mount point:
```
sudo chown -R **your_username:your_username** /media/ext3
```maybe you need to chown after you mount the partition
4.) remount the partitions:
```
sudo umount /dev/sda1
sudo umount /dev/sda2
sudo umount /dev/sda3
sudo mount -a
```ignore the "umount: /dev/sdaX: not mounted" 

5.) make sure you are in the plugdev group:
```
sudo usermod -a -G plugdev **your_username**
```

---

### Post by jw5801 on 2008-02-28
Guys, he only wanted to have his ext3 storage partition mount, not the ntfs partitions. So no, ntfs-3g isn't going to help :p

---

### Post by tootlet on 2008-02-28
Thanks,
JW was right, I only wanted access to  the sda3 partition which is ext3 formated. Here's what I had to do to get it to work. (Thanks for the advice)
sudo gedit /etc/fstab
added to fstab:
/dev/sda3 /mnt/data ext3 rw 0 2
Again thanks for the advice as having the file system checked is highly desirable and I didn't know that. 

Still no access. When I tried to cd into /mnt/data I got no such directory. So:
sudo mkdir /mnt/data

Now I could get to /mnt/data and read only. Hmmm. 

sudo chown tootlet /mnt/data 

I could then read all of the folders/files in /mnt/data but not write to subfolders. Still not what I wanted!

sudo chown -R tootlet /mnt/data
  
Success! I can now read and write to sda3 and have added about 160 Gb of storage area. 

I appreciater all the help.

Tom  :)

---

