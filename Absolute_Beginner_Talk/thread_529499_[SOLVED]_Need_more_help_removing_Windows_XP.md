---
title: "[SOLVED] Need more help removing Windows XP"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by cwrann on 2007-08-19
I want to remove Windows XP from my compoter, I gather that the only way to do this is to unmount and reformat the partition so that the space can be used by Ubuntu. I have tried two methods.

1st I tried gparted to unmount that the partition sda1 (this has windows on it) I get an error message telling me:

[B]The partition could not be unmounted from the following mountpoints:
/media/sda1
Most likely other partitions are also mounted on these mountpoints. You are advised to unmount them manually.[/B]

2nd I tried a method that I had found in a previous post:

**sudo gedit /boot/grub/menu.lst**

I edited out all mentions of windows then:
[B]
 sudo fdisk -l[/B]

[B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15935   127997856    7  HPFS/NTFS
/dev/sda2           15936       44618   230396197+   7  HPFS/NTFS
/dev/sda3           44619       60728   129403575   83  Linux
/dev/sda4           60729       60801      586372+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS[/B]

and

[B]sudo mkfs.ext3 /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted; will not make a filesystem here![/B]

Does anybody know what I'm doing wrong?

---

### Post by taurus on 2007-08-19
Try

```
sudo umount /dev/sda1
```
And if you still get the same error message, post

```
df -h
cat /etc/fstab
```

---

### Post by cwrann on 2007-08-19
WOW fast and accurate!!!
 
sudo umount /dev/sda1

Worked great, I then went into gparted and formated the partition space to ext3.

Any idea why I was having trouble in the first place?

---

### Post by cwrann on 2007-08-19
Any Idea what the lost+ found folder with contents that I cannot view is and how do I name the Icon to sda1. Right now it just says Disk

---

### Post by taurus on 2007-08-19
I think the problem lied with gparted.  When you ran gparted, /dev/sda1 was already mounted to /media/sda1 so technically, gparted was accessing /media/sda1 so you couldn't unmount it from gparted while it is using it.  Therefore, you need to umount it by hand first.

Lost+found is part of ext2/ext3 filesystem.  It is used system to store lost data in case there is a damage to the partition.  So, I would recommend you leave that alone since it doesn't take up any space at all.

---

### Post by cwrann on 2007-08-19
Sorry I think my second question got lost in my last post. The icon for my newly formatted drive is just "**drive**" but under gparted it is named "**sda** 1". How do I change "**drive**" to **sda 1**

---

### Post by cwrann on 2007-08-19
The sda1 Icon on the desktop was titled Disk. When I rebooted the icon is nowhere to be found. In gparted it is listed as /dev/sda1 and it is mounted as /mnt/storage. how do I access this partition?

Am I missing something basic, am I not supposed to be able to see it as an Icon on the desktop?

---

### Post by taurus on 2007-08-19
Applications -> Accessories -> Terminal
```
ls -la /mnt/storage
```
Or use nautilus and navigate to /mnt/storage.

---

### Post by cwrann on 2007-08-20
I appreciate all of the help and don't mean to bug you (If it's any consolation I just got [I]The official Ubuntu book [I][/and will read it immediately).

This is what I get from the code:

 ls -la /mnt/storage
total 24
drwxr-xr-x 3 root root  4096 2007-08-19 18:34 .
drwxr-xr-x 3 root root  4096 2007-08-19 18:26 ..
drwx------ 2 root root 16384 2007-08-19 18:34 lost+found

from this I figured that I should navigate into the FileSystem and look in the mnt folder. The storage drive is there but it only has 113.9 GB the partition that we have been talking about has 122.07 GB. Also when I tried to drop files into the storage it told me I do not have permission to write in it.

Also, the partition we have been discussing used to be called sda1, this file is still in the media file under Filesystem but it is now empty and the to GB of this file is 110.2GB, this file size as well as the storage file size don't match up with any of my partitions.

I want to consolidate all of my multimedia files  to one partition this is why I wanted to free up that partition.

The other question I had was is there a way to make a shortcut from the desktop to the partition?

 I know that these are very basic problems that are the result of a twelve years on windows.

thanks again for all of your help.

---

### Post by taurus on 2007-08-20
Post

```
df -h
```
If you want to be able to write to /mnt/storage without becoming root, using sudo, you need to change the ownership of /mnt/storage from root to your login name.  For now, I will _assume_ your login name is **john** so make sure you subs in the right one.

```
sudo chown -R **john**:**john** /mnt/storage
ls -la /mnt
```

---

### Post by cwrann on 2007-08-20
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             122G  5.1G  111G   5% /
varrun               1006M  108K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
procbususb           1006M   96K 1006M   1% /proc/bus/usb
udev                 1006M   96K 1006M   1% /dev
devshm               1006M     0 1006M   0% /dev/shm
lrm                  1006M   39M  968M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2             220G  214G  6.3G  98% /media/sda2
/dev/sdb1             150G  103G   47G  69% /media/New Volume
/dev/sda1             121G  646M  114G   1% /mnt/storage

sda1 shows up as 121G here why does it show up as another amount in properties?

---

### Post by cwrann on 2007-08-20
df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             122G  5.1G  111G   5% /
varrun               1006M  108K 1006M   1% /var/run
varlock              1006M     0 1006M   0% /var/lock
procbususb           1006M   96K 1006M   1% /proc/bus/usb
udev                 1006M   96K 1006M   1% /dev
devshm               1006M     0 1006M   0% /dev/shm
lrm                  1006M   39M  968M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda2             220G  214G  6.3G  98% /media/sda2
/dev/sdb1             150G  103G   47G  69% /media/New Volume
/dev/sda1             121G  1.3G  113G   2% /mnt/storage

So basically 
sda3 is what I partitioned off to run ubuntu
sda2 is an ntfs partition 
sdb1 is and external ubs drive
sda1 is listed under mnt/storage but also appears under the "media" file right next to sda2 and when I got to the properties option of both the mnt and the media I get a GB size that is inconsistent with what I am reading here.

---

