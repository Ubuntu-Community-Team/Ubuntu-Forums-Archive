---
title: "Can't access NTFS partitions"
date: 2006-08-18
forum: Absolute Beginner Talk
---

### Post by clint37 on 2006-08-18
I'm new to Ubuntu and Linux. I've installed Ubuntu on a second hard drive. Windows XP is installed on the first one. Dual boot works fine, everything is great - except:

I can't access my NFTS partitions on the first HDD from Ubuntu. 

When I go into Disks Manager, it recognises that both HDDs are there, and recognises all the partitions, but the NFTS partitions say:
Filesystem: Unformatted
Access Path: blank
Staus: Inaccessible (clicking Enable isn't working)

I know I can't write to NFTS, I just want to be able to access the files on there. What do I do?

Thanks in advance,
Clint

---

### Post by ComplexNumber on 2006-08-18
can you print out the contents of fstab(you will find it at /etc/fstab) and post it here?

---

### Post by CREEPING DEATH on 2006-08-19
[This works]("https://help.ubuntu.com/community/MountingWindowsPartitions"), in fact I just did it yesterday.

CD

---

### Post by rck_hitokiri on 2006-08-19
all you need to do is configure yout fstab which you can access via terminal. applications > accessories > terminal. in the terminal type:

code:
sudo mkdir/windows - this makes a directory mount for your ntfs.
sudo nano /etc/fstab
after coming to the fstab module type this:
/dev/hda /windows ntfs nls=utf8 umask=0222 0 0

assuming that your ntfs partition is on your primary master you should type /dev/hda1 as i have typed here if not it could be hb1, hdd, etc....

it would be better if you posted your fstab here.
terminal type sudo nano /etc/fstab and copy paste it here.
thanks hopes this helps, cheers.

---

### Post by givré on 2006-08-19
And if you don't know the name of your partition, just type
```
sudo fdisk -l
```
in a terminal.
But check CREEPING DEATH link, he is quite good :cool:

---

### Post by clint37 on 2006-08-19
Thanks for the replies. I followed the directions from the link suggested by Creeping Death but it didn't work. I want to read hda1, hda5 and hda6.

My fstab file reads thusly:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by givré on 2006-08-19
Ok so, what you need to do is :
- create a directory for each partition in /media. You'll have to do that via the terminal because it require root privilege :
```
sudo mkdir /media/<the name you want, like windows, data,...>
```
- add at the end of your /etc/fstab 
```
gksu gedit /etc/fstab
```
the following line for each partition
```
/dev/<your partition> /media/<the mount point> ntfs nls=utf8 umask=0222 0 0
```
The mount point is just the directory you just create.
- save and close
- mount everything
```
sudo mount -a
```

---

### Post by clint37 on 2006-08-19
Thanks Givre

I'm making progress but not there yet, here's what happened:

I followed your instructions, now my NTFS partitions are showing up in Disks Manager, unlike before. It says 
Filesystem: Windows NTFS
Access Path: /media/windows1
Status: inaccessible (enable still not working)

When I try to mount everything using sudo mount -a
 I get the following response:
[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 9 in /etc/fstab is bad
[mntent]: line 10 in /etc/fstab is bad

There's probably a slash in the wrong place or something, I wouldn't know

My fstab now looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /media/windows1 ntfs nls=utf8 umask=0222 0  0
/dev/hda5       /media/windows2 ntfs nls=utf8 umask=0222 0 0
/dev/hda6       /media/windows3 ntfs nls=utf8 umask=0222 0 0

---

### Post by givré on 2006-08-19
> **clint37 said:**
> 
/dev/hda1       /media/windows1 ntfs **nls=utf8 umask=0222** 0  0
/dev/hda5       /media/windows2 ntfs **nls=utf8 umask=0222** 0 0
/dev/hda6       /media/windows3 ntfs **nls=utf8 umask=0222** 0 0
nls & umask are two option, they shouldn't be separtate by a space.
You should replace that by :
> **clint37 said:**
> 
/dev/hda1       /media/windows1 ntfs **nls=utf8,umask=0222** 0  0
/dev/hda5       /media/windows2 ntfs **nls=utf8,umask=0222** 0 0
/dev/hda6       /media/windows3 ntfs **nls=utf8,umask=0222** 0 0
And remount all ;)

---

### Post by clint37 on 2006-08-19
Thanks again, that fixed the error, but now when i mount all it says:
mount: special device /dev/hda1 does not exist
mount: special device /dev/hda5 does not exist
mount: special device /dev/hda6 does not exist

even though they're all listed in Disks Manager

---

### Post by givré on 2006-08-19
Disk manager basicly show what you put in /etc/fstab, so if fstab is wrong, disk manager also.
To check the name of your partition, just  do a 
```
sudo fdisk -l
```

---

