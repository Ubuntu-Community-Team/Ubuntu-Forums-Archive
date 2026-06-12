---
title: "How to mount a partition"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by Nvening on 2006-12-13
Hi, i just formatted a partition into ext3 however i now dont know how to mount it?

I found one command on another site however it didnt work as it did not accept ext3 as the file system.

Thanks

---

### Post by linuchsan on 2006-12-13
How did you mount it?

---

### Post by jonny123 on 2006-12-13
Hi mate,

I'll try to help

Need to open a terminal/shell.

try these this - use sudo in front which is superuser. May ask for you admin pass.


"mount" will show mounted partitions.

You have to make a folder to link to the partition
ex. "mkdir /mnt/partition2"

Load settings > disks ( Gnome> System > Disks )

Click partitions, it will show where hard disk is located ex. /dev/hda2
So you will mount like this "mount /dev/hda2 /mnt/partition2"
"cd /mnt/partition2" and "ls" to List files (Dir in dos)

Reply is this helps

Jon

---

### Post by linuchsan on 2006-12-13
**mount /dev/hd?? /mount/point** for ata, or **/dev/sd?? /mount/point **for sata

---

### Post by taurus on 2006-12-13
> **Nvening said:**
> Hi, i just formatted a partition into ext3 however i now dont know how to mount it?

I found one command on another site however it didnt work as it did not accept ext3 as the file system.

Thanks
If you can tell me what partition you want to mount, (/dev/hda1, dev/hdb1, /dev/sda1, /dev/sdb1, or whatever), then maybe I can show you how to add it to your /etc/fstab so that it would be mounted automatically each time you boot...

---

### Post by Nvening on 2006-12-14
I am familiar with fstab so if you gave me the command to put in then i would be able to do the rest.

However i am not sure the name of the partition i need to mount, how do i get a list of drives which are not mounted?

EDIT: from looking at the mount command i think is dev/sda3 but im not completely sure.

Thanks

---

### Post by taurus on 2006-12-14
```
sudo fdisk -l
```

---

### Post by Nvening on 2006-12-14
ok its 

/dev/sda5

and the mount point is /media/Media

Thanks

---

### Post by taurus on 2006-12-14
> **Nvening said:**
> ok its 

/dev/sda5

and the mount point is /media/Media

Thanks
Is it ntfs or fat32?

---

### Post by Nvening on 2006-12-14
its ext3, i can mount NTFS drives just not normal ones! (lol)

---

### Post by taurus on 2006-12-14
Okay, fire up a text editor and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it...

```
/dev/sda5   /media/Media   ext3   defaults   0   2
```
Save it and mount it with

```
sudo mount -a
df -h
```

---

