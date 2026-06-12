---
title: "External Hard Drive Issue"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by zutronius on 2007-07-06
I am running Ubuntu Studio 7.0.4 and I use an 80 gb external drive to back up all of my info. However, the external drive at the empty at the moment, yet only shows 22.7 gb of free space. I would like to format it so I can use all 80gb of the drive (I'm only limited to the 22.7 gb for some reason).

How do I go about doing this?

---

### Post by Cypher on 2007-07-06
Was the drive formatted previously? What filesystem was on it?

---

### Post by zutronius on 2007-07-06
The drive was previously used on my pc which had XP (the cd  was scratched beyond use by a 5 year old).

---

### Post by zutronius on 2007-07-06
It was also I believe the FAT system as well.

---

### Post by Cypher on 2007-07-06
Hmm, well it was probably FAT32 cuz regular FAT can't see anywhere near 80G. How did you check in Ubuntu to  see that it was only seeing 22G of the 80G??

---

### Post by zutronius on 2007-07-06
I have the drive empty and I tried to transfer my 35 gig worth of music onto my drive. I get a message saying there is not enough room for my files.

I right clicked on the drive just to see how much space was showing as being available and it only showed me that 22.7 gig were free.

---

### Post by Cypher on 2007-07-06
AHh Ok..can you open up a terminal and do
```

sudo fdisk -l
mount
df -h

```
and show us the output..

---

### Post by zutronius on 2007-07-06
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       11903    95610816   83  Linux
/dev/hda2           11904       12161     2072385    5  Extended
/dev/hda5           11904       12161     2072353+  82  Linux swap / Solaris

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9728    78140128+   c  W95 FAT32 (LBA)


 Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        9728    78140128+   c  W95 FAT32 (LBA)
zutronius@emachines:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-lowlatency/volatile type tmpfs (rw)
/dev/hdd on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=zutronius)
/dev/sde1 on /media/WD USB 2 type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

dev/sde1              75G   39G   36G  53% /media/WD USB 2
The above line has me baffled. The drive is empty, yet is showing the above stats?

---

### Post by Cypher on 2007-07-06
So it's seeing the 80G physucally, but it thinks that about 39G is in use..can go you do the following in the terminal
```

cd /media/WD
du -sch *

```
This should hopefully tell us where the space is going, hopefully..

---

### Post by zutronius on 2007-07-06
zutronius@emachines:~$ cd /media/WD
bash: cd: /media/WD: No such file or directory

zutronius@emachines:~$ du -sch *
24K     amsn_received
50G     Desktop
220K    Firefox_wallpaper.png
1.4M    Sarah
4.0K    Shared
50G     total

---

### Post by Cypher on 2007-07-06
OK, now I'm confuzzled..it's obivously mounted /dev/sde1 on /media/WD..strange..ok let's try
```

cd /media
ls -l

```

---

### Post by zutronius on 2007-07-06
/dev/sde1              75G   39G   36G  53% /media/WD USB 2

---

### Post by zutronius on 2007-07-06
Ok here we are...

zutronius@emachines:~$ cd /media
zutronius@emachines:/media$ ls -l
total 38
lrwxrwxrwx  1 root      root     6 2007-06-16 08:06 cdrom -> cdrom0
dr-xr-xr-x 10 root      root  2048 2007-05-10 02:12 cdrom0
drwxr-xr-x  2 root      root  4096 2007-06-16 08:06 cdrom1
drwx------  5 zutronius root 32768 1969-12-31 19:00 WD USB 2

---

### Post by Cypher on 2007-07-06
Aha..OK now (you'll be an expert with the command line after this..:) )
```

cd /media
sudo chmod 755 WD
cd WD
du -sch *

```

---

### Post by zutronius on 2007-07-06
Hit a snag :(

zutronius@emachines:/media$ sudo chmod 755 WD
chmod: cannot access `WD': No such file or directory

---

### Post by Cypher on 2007-07-06
AHA! I'm sorry..I can't read..
```

cd /media
sudo chmod 755 "WD USB 2"
cd "WD USB 2"
du -sch *

```
Put the directory name in quotes because it has spaces in it..

---

### Post by zutronius on 2007-07-06
It was working fine until the laast command line.

zutronius@emachines:/media/WD USB 2$ du -sch *
du: cannot access `*': No such file or directory
0       total

---

### Post by Cypher on 2007-07-06
OK..let's try again..
```

cd /media
sudo chmod -R 755 "WD USB 2"
cd "WD USB 2"
ls -l
du -sch *

```

---

### Post by zutronius on 2007-07-06
zutronius@emachines:/media/WD USB 2$ cd /media
zutronius@emachines:/media$ sudo chmod -R 755 "WD USB 2"
zutronius@emachines:/media$ cd "WD USB 2"
zutronius@emachines:/media/WD USB 2$ ls -l
total 0
zutronius@emachines:/media/WD USB 2$ du -sch *
du: cannot access `*': No such file or directory
0       total
zutronius@emachines:/media/WD USB 2$

---

### Post by Cypher on 2007-07-06
OK so basically the "ls -l" confirms that the drive is empty, do a "ls -la" just for grins to see if there are any hidden files. Not sure what is taking up ~30+ Gigs here..confusing..

---

### Post by zutronius on 2007-07-06
AHA

total 196
drwx------  5 zutronius root 32768 1969-12-31 19:00 .
drwxr-xr-x  5 root      root  4096 2007-07-06 11:15 ..
-rwx------  1 zutronius root 21508 2007-01-10 17:45 .DS_Store
drwx------  2 zutronius root 32768 2007-01-10 17:44 .Trashes
-rwx------  1 zutronius root  4096 2007-01-10 17:44 ._.Trashes
drwx------  2 zutronius root 32768 2007-01-11 20:15 .Trash-zachman
drwx------ 11 zutronius root 32768 2007-07-06 11:10 .Trash-zutronius

---

### Post by Cypher on 2007-07-06
OK..we're going get to the end of this one way or another..:)

Go through each of those directories and do a "ls -la" and see what's in there..I'm going to guess that you have stuff stuck in there you can delete to regain all your space..

---

### Post by zutronius on 2007-07-06
This is no doubt going to be a stupid question, but how do I go through each of those directories?

This is day 3 of Linux for me.

---

### Post by twiceasworn on 2007-07-06
You can change directories by using "cd <directoryname>" (obviously without the brackets.).  Then just do the "ls -la" command.  It is strange that those hidden files would be taking up 30 gig though.  I mean, if there isn't anything on it you need, I would just re-format the drive.  But thats because I am lazy.

---

### Post by zutronius on 2007-07-06
How do I reformat the drive? I have everything off it that I want. A format would spare us some headaches I think. I gotta thank you for being patient with me as well!

---

### Post by ButteBlues on 2007-07-06
> **zutronius said:**
> How do I reformat the drive? I have everything off it that I want. A format would spare us some headaches I think. I gotta thank you for being patient with me as well!
```
sudo apt-get install gparted
```

Then:

```
gksu gparted
```

When it starts, select the external HDD in the top right corner, then choose to unmount it, and then right click on the partition entry in the main area and choose "Format to > ext3".

---

### Post by zutronius on 2007-07-06
I attempted to unmount it and I got the following error emssage:

umount: /media/WD USB\0402: not found

---

### Post by Cypher on 2007-07-06
The spaces in the filename are just going to be a pain..but do the following in the terminal
```

cd /
sudo umount "/media/WD USB 2"

```

---

### Post by zutronius on 2007-07-06
zutronius@emachines:/$ sudo umount "/media/WD USB 2"
umount: /media/WD USB 2: not found
zutronius@emachines:/$

---

### Post by zutronius on 2007-07-06
Sorry guys,

I gotta head to school for the next 8 hours. Thanks for all the help. This has me more than baffled thats for sure.

---

### Post by ButteBlues on 2007-07-06
> **zutronius said:**
> I attempted to unmount it and I got the following error emssage:

umount: /media/WD USB\0402: not found
Did you try to unmount it in Gparted or in the terminal?

---

