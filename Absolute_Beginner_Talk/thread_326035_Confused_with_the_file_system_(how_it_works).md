---
title: "Confused with the file system (how it works)"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by kinson on 2006-12-26
Hi guys,

Actually this is a weird question(to me). Roughly I know the hierarchy of the file system("/" being the top, then hard disk's under "media" or something like that etc etc). I'm honestly more familiar with windows file system(c:\, d:\ etc etc).

I'm just curious how it works. Cause in windows, if I had 2 partitions(physical or not), I'll have a C drive and a D drive, and windows operating system will be in C drive. so roughly I know how much space it uses.

But in linux, "media"(or the hda hdb etc etc) are UNDER root? So I'm a little lost....assuming I allocate 3gb for Ubuntu, does that mean that "root has 3gb"? And then mounts the disks under "media"? How would I be able to know how much space root is using for instance? I know I sound confused :p But I'm just having a little problem understanding the whole thing :p


Cheers,
Kinson

---

### Post by taurus on 2006-12-26
Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by macogw on 2006-12-27
C:\ and D:\ are just what Windows names the drives to differentiate them.  They're still part of the file system hierarchy.  C:\ is like /, and then A:\ and D:\ and everything are sort of shorthand for /media/floppy and /media/cdrom0.  If you make / be on partition1 and /home be on partition 2, then you'd have / with /dev/hda2/home.  It wouldn't LOOK like that, you'd still see /home, but that's a symlink (symbolic link), like a shortcut on the Windows desktop.

---

### Post by michaeljustman on 2006-12-27
Just think of '/mnt/' as 'My Computer' in windows. C:,D:, etc all show up under 'My Computer'. The only difference is root is also kind of like 'C:\Windows\" too in that it has all the files in it that make the operating system work.

The files on '/' take up space just like the files in 'C:/Windows/' take up space. The hard drives you have plugged in or the partitions that aren't '/' are just mounted (given a place, for you to refer to them) and have thier own capacity, etc.

I'm sorry. I'm probably not making much sense either.

---

### Post by dasunst3r on 2006-12-27
Oh, boy... just you wait until you get into NFS mounts.  You could easily have something like /home/user somewhere else!

In any case, here's my understanding of how Linux handles different partitions:
1. Each **physical** device is assigned a letter in the device space (/dev).  For example, your first drive would be hda, second drive would be hdb, and so on.
2. Each **partition** on each drive is then assigned a number, again, in the device space.  Therefore, suppose you have two partitions on your first drive.  The two partitions would be located at /dev/hda1 and /dev/hda2
3. These devices can be mounted anywhere.  For all you know, I could have /dev/hdb1 be mounted to /home, /dev/hda1 be swap, and /dev/hda2 be / (i.e. everything else)

Hope this helps.

---

### Post by kinson on 2006-12-27
Thanks for all the replies(and extremely fas too :p )

I guess my main confusion stems from the fact that I'm looking at root as the whole thing, and the mounted drives as inside root. But yet I know that root must somehow be contained *inside* one of the disks(its obviously on a physical disk), but yet in the file system, it shows up as *outside* the physical disk(cause /dev/hda is within "/"). Confusing :p

I suppose I'll need to take some time and digest this information :p but I think the concept of symlinks is something that I just learnt here, so I think I'll need to read up more on symlinks to understand this perhaps :s

Cheers,
Kinson

---

### Post by towsonu2003 on 2006-12-27
df -h , and baobab are nice tools to get a picture of how much space you're using. 

> But in linux, "media"(or the hda hdb etc etc) are UNDER root? So I'm a little lost....assuming I allocate 3gb for Ubuntu, does that mean that "root has 3gb"?

my 2cents:
imagine you have just 1 partition:

partition 1: / (39GB)

Than / = C: = 39GB

--------------------------------------

now imagine you've got 4 partitions, and a floppy drive and all of them are mounted. 

imagine you mounted them like this:
partition 1: / (9GB)
p 2: /home/user (10GB)
p 3: /media/windows (15GB)
p 4: /var (5GB)
floppy: /media/floppy (1MB)

For Linux, it's still / = C: = 39GB

However, now that for instance /home/user is mounted in some other partition, its size limitation is independent (10GB). Same goes for others. 

--------------------------

Another example: 

/var/log is a "folder" that has log files, and when running a server, you get all the logs of the server in there. you installed a server. and one day you got too many visitors at once to your server, which made the log files soooo big, your / got full and your server crashed, unable to write data to disk. Moreover, everytime you bring the server up, because now you're so popular, /var/log goes crazy on you. 
So you do: 

2 partitions:
p 1: / (10GB)
p 2: /var/log (29GB)

/ is still 39GB, but now /var/log can not get bigger than 29GB no matter what. 

-----------------------------

/media (aka /mnt in other distros) is where external devices are mounted. so if you insert a cdrom, you will get /media/cdrom, or for a floppy, /media/floppy, and for a usb drive, /media/usbdisk... it's still under / , but its also a device of its own.

[edit: shockingly, I wrote this thing in 25 minutes or so... ouch!]

---

### Post by kinematic on 2006-12-27
it's really quit simple.
with linux everything is a file or a folder.
a mountpoint is just an insertion point into the root fileystem to access a partition,harddrive,cd drive or some other device.
you can mount a hdd or partition anywhere you want....if you would want to mount lets say /dev/hda3 as a hidden partition you could mount it at  /home/.hda3 or /media/.hda3(the period in front of hda3 means that it's hidden and it will show up if you check the "show hidden files" box in nautilus or konqueror).
so that's all a mountpoint is....an insertion point into the root file system for access.
and i'll throw in a picture of the file system layout ;)

---

### Post by kinson on 2007-01-02
I think I understand now :p thanks for all the replies. :)

Cheers,
Kinson

---

