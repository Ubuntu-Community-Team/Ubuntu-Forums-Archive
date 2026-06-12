---
title: "Is there a way to mount hda1 on the livecd?"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by Rackerz on 2007-01-22
My HDD's aren't automatically loaded when the livecd boots, I try sudo mount /dev/hda1 but it says that it's not in fstab. How do I mount the drive?

---

### Post by taurus on 2007-01-22
I assume your /dev/hda1 is ntfs then.

Applicatons -> Accessories -> Terminal
```
sudo mkdir /media/hda1
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222 0 0
df -h
```

---

### Post by Rackerz on 2007-01-22
I ran this;
```
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=022
```

It returned;

> ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222 0 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by taurus on 2007-01-22
Forget about the two zeros at the end.

```
sudo mount -t ntfs /dev/hda1 /media/hda1 -o nls=utf8,umask=0222
```

---

### Post by Rackerz on 2007-01-22
Thanks that worked :D. But I can't write to my external drive (NTFS). I've got a partition formatted to ext3 where I can backup my files. Do I need a new command to mount it or can I change the ntfs around to ext3 or does it not work like that?

Thanks

---

### Post by taurus on 2007-01-22
You cannot write to ntfs right now unless you install ntfs-3g driver first.  

What partition is that ext3 resided.  It would look something like

```
sudo mkdir /media/hda2
sudo mount -t ext3 /dev/hda2 /media/hda2
```
And if you want to write to /media/hda2 as a regular user (without using sudo), then you just change the permission to /media/hda2 or make yourself the owner of /media/hda2.

---

### Post by Rackerz on 2007-01-22
Thanks that also worked, usually I'm not good with the command line. How do I make myself owner so I can simply copy and paste? 

Thanks

---

### Post by taurus on 2007-01-22
Is there anything on /dev/hda2?  what's the output of this command from a terminal?

```
id
```

---

### Post by Rackerz on 2007-01-22
I did a quick search just now and did a chown. The files are copying over now (correctly I hope). Thanks again for putting up with my silly questions.

---

