---
title: "FULL disk problem"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-03-06
Hi
 I need real help. I copied a backup tar file to a External hard drive and now I have o zero space on the external hard drive.

When I look at the external  drive and click on it to delete , it goes away.

How do I remove  the backup file on the external disk?

---

### Post by Lord Illidan on 2006-03-06
Enable show hidden files in Nautilus or Konqueror, depending if you are using GNOME/KDE.

Then go to a folder named .Trash

And see if you can clear it out.

---

### Post by kent41 on 2006-03-06
Thanks 
I enabled  hidden files but I only see the original 1 file that has it name messed up.

Is there some way I can  use a terminal mode to access the external drive and delete some files?

When I enter /dev/sda1  I get error that I don't have permissions.
When I enter   chmod 777 /dev/sda1  I get no error

Is there some way to salvage this disk?

---

### Post by kent41 on 2006-03-06
**Bump**

---

### Post by taurus on 2006-03-06
[QUOTE=kent41]Thanks 
I enabled  hidden files but I only see the original 1 file that has it name messed up.

Is there some way I can  use a terminal mode to access the external drive and delete some files?

When I enter /dev/sda1  I get error that I don't have permissions.
When I enter   chmod 777 /dev/sda1  I get no error

Is there some way to salvage this disk?[/QUOTE]
Try

```

cd /dev/sda1
sudo rm <filename>

```

---

### Post by kent41 on 2006-03-06
[QUOTE=taurus]Try

```

cd /dev/sda1
sudo rm <filename>

```[/QUOTE]

taurus this is what i get from entering code
```

kent@GPS-2:~$ cd /dev/sda1
bash: cd: /dev/sda1: Not a directory
kent@GPS-2:~$ sudo rm backup.tgz
Password:
rm: cannot remove `backup.tgz': No such file or directory
kent@GPS-2:~$



```

---

### Post by taurus on 2006-03-06
Is your external drive /dev/sda1 and do you have it mount right now?  What is the output of this command, from a terminal
```

df -h

```

---

### Post by kent41 on 2006-03-06
When I try to mount sda1 I get 


[/CODE]
```

kent@GPS-2:~$ sudo -s -H
root@GPS-2:/home/kent# mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
root@GPS-2:/home/kent#

```

I also don't know how or what to add to /etc/fstab

Code:
```

[CODE]kent@GPS-2:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  1.9G   15G  12% /
tmpfs                 236M     0  236M   0% /dev/shm
tmpfs                 236M   13M  224M   6% /lib/modules/2.6.12-10-386/volatile
kent@GPS-2:~$
```

---

### Post by taurus on 2006-03-06
You don't have /dev/sda1 mounted so you need to do this,
```

sudo mkdir /mnt/external
sudo mount -t vfat /dev/sda1 /mnt/external
cd /mnt/external
sudo rm <filename>

```
(Assuming that your external drive is vfat or fat32 format...  If it's an ext3 filesystem, then replace the vfat with ext3 from the above mount command.)

---

### Post by kent41 on 2006-03-06
I think the file format was ext3 because the external drive was bootable if in inserted it into the computer as the only hard drive.

here is what happened when I tried to MOUNT
```

root@GPS-2:/home/kent# sudo mkdir /mnt/external
root@GPS-2:/home/kent# sudo mount -t ext3 /dev/sda1 /mnt/external
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@GPS-2:/home/kent# sudo mount -t vfat /dev/sda1 /mnt/external
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

root@GPS-2:/home/kent#

```

---

### Post by taurus on 2006-03-06
Are you sure it's ext3?  It could be ext2 or even reisfs.  By the way, what does "dmesg | tail" say?  Or you can also try 
```

sudo mount /dev/sda1 /mnt/external

```
Also, what does your /etc/fstab look like anyway?

---

### Post by kent41 on 2006-03-06
When the external drive was in the computer it had the same file type ext3


This is my current** fstab** on the internal drive 

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by kent41 on 2006-03-06
This looks BAD

[ATTACH]6802[/ATTACH]

---

### Post by syg00 on 2006-03-06
What does "fdisk -l /dev/sda" return ???. (that's ell, as in list)

---

### Post by kent41 on 2006-03-06
Not much
```

root@GPS-2:/home/kent# fdisk -l /dev/sda
root@GPS-2:/home/kent#

```

It looks like to me when I copied the  tars backup to the external dirve it wrote over the file system even though there was 2.33 gig of free space, and the backup file was only 1.9 gig in size.

If a OS allows you to copy a file to a disk and it copies over the OS ,  that looks like a serious BUG.

*

---

### Post by syg00 on 2006-03-07
Mmmmm - I suspect you may have copied the file to /dev/sda, rather than to a mount-point (say /mnt/sda1).
Hard to tell from here. I'd be inclined to use fdisk to delete everything and recreate any (and all) partitions again.

Your choice.

---

