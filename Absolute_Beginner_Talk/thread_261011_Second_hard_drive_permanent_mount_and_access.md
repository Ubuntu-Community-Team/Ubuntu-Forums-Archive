---
title: "Second hard drive permanent mount and access"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by ClarkePeters on 2006-09-19
I always keep two hard drives in my system, one for the operating system and one for data and data backups and such.
The first time I installed Ubunty I didn't have my secondary hard drive plugged in so that Ubuntu didn't recognize it.
After I plugged it in, Ubuntu found it, but as a read only disk, I could write, save new files, or delete old files (I wasn't the owner, it said, phht! I am too! haha) Well, I did a lot of research on how to mount and get access to my own drive etc.. only later to find out that if I had plugged in my secondary disk BEFORE the install, Ubuntu would automatically recognize it, permanently mount it and give me total access.


Lesson learned: ***Plug in your secondary hard drive before your Ubuntu install***

---

### Post by ClarkePeters on 2006-09-19
I meant to say I could NOT write, save new files, delete old files ......

---

### Post by Sonic Alpha on 2006-09-19
If it is formatted to NTFS, I don't believe you will be able to write to the disk.  You can write to a FAT partition though.

---

### Post by deadspeak on 2006-09-19
i've had this same problem, acouple of times, initially thought it was the ntfs thing, but even with the drive formatted in FAT32 it still won't mount, the only way i found was to reinstall ubuntu, luck it's pretty painless

---

### Post by bodhi.zazen on 2006-09-19
fstab anyone?

---

### Post by edm1 on 2006-09-19
it sounds like all you need to do is edit fstab. [this]("http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28FAT.29_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite") guide may help.

---

### Post by ClarkePeters on 2006-09-20
In my case, the secondary hard drive is not NTFS. It is a Fat32. It was a while, though, before I figured out that my NTFS drives are only accessible as a read-only device. So thank you for the heads up, others may not realize this. For this reason, I keep all my drives formatted to Fat32.

True, in some cases the install may not recognize the secondary hard drive even if it is plugged in, though mine usually does ( I have noticed that if I  have too many USB devices plugged in, i.e. printer, that it will skip the hard drive, or so it seems). In those cases, of course, you will need to edit the fstab.  

sudo gedit /etc/fstab

then add a line like this one to the file:
/dev/hdb1   /media/hdb1  vfat  defaults,utf8,umask=007,gid=46 0  1

of course, this particular line may not work for everyone, but you could copy and paste it and give it a shot. It won't hurt, you can take it out later if it doesn't work-- or comment it with a # as the first character in the line to keep it; and then find out what your particular options etc. should be.

The above line both mounts and makes the disk acessible for the administrator.

---

### Post by bodhi.zazen on 2006-09-20
```
/dev/hdb1 /media/hdb1 vfat user 0 0
```

Is easier and is how most Ubuntu users (or at least noobs) want to mount their partitions.

[How to edit fstab](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by ClarkePeters on 2006-09-20
easier is always better.

by the way, if one does have to add this line to your etc/fstab
make sure you create a directory
/media/hdb1

I forget to do this nearly every time.

---

### Post by infoseeker on 2006-09-20
I find that it is a lot easier creating a directory under your own home partition (that is if you are the only user on the PC)

```
~ $ mkdir ~/<name>
```
where <name> could be 'hdc1', or 'data' as example.

which means no changing to /media/<name> each time you want to access the drive.  Simply the add the path in fstab.

---

### Post by bodhi.zazen on 2006-09-20
> **infoseeker said:**
> I find that it is a lot easier creating a directory under your own home partition (that is if you are the only user on the PC)

```
~ $ mkdir ~/<name>
```
where <name> could be 'hdc1', or 'data' as example.

which means no changing to /media/<name> each time you want to access the drive.  Simply the add the path in fstab.

I mount in /mnt.

If you mount in /media the drive will appear on the desktop when mounted. Most users seem to like this, I run a clean desktop.

At any rate, rather then mount in /home use a link:

```
ln -s /media/hdb1 ~/hdb1
```

Of course you can call the mount point or link what you will ```
ln -s /media/hdb1 ~/Hi_mom
``` will create a directory in you home "Hi_mom" which will link to /media/hdb1 which is of course /dev/hdb1....

Does anyone see the humor in "mount Hi_mom" ? Just don't skip the Hi.

---

