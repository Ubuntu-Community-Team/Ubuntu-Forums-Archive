---
title: "ATI X1300 resolution"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by Hughsy on 2007-07-31
Hi, 
Im new to Ubuntu, but I seem to have successfully installed my x1300 as per the fglrxinfo below. The problem is that I cant change my screen resolution to anything above 1024x768, but I know my monitor supports higher resolutions. 

I'd appreciate any tips/help. If I need to provide any specific details, please ask. I searched the forums before posting and cant seem to see anything relating to this problem. 
I followed the instructions posted in the forum. 


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1300/X1550 Series
OpenGL version string: 2.0.6334 (8.34.8)

---

### Post by Ek0nomik on 2007-07-31
Backup your xorg.conf file;

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Reconfigure your xserver, using the spacebar to select item(s);

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Enjoy more pixels;

```
echo thanks Ek0nomik
```

:)

---

### Post by Hughsy on 2007-07-31
> **Ek0nomik said:**
> Backup your xorg.conf file;


```
echo thanks Ek0nomik
```

:)

/echoed :)

---

### Post by Ek0nomik on 2007-07-31
> **Hughsy said:**
> /echoed :)

:)

I take it you got it working?  If so, excellent!

---

### Post by Hughsy on 2007-07-31
I did, thank you very much. It was straight forward enough. 
Actually I'd appreciate a little more help on something. I want to set permissions, but the options are greyed out. 
Ive attached a screenshot to show what Im talking about. 

Cheers for such quick answers btw. Really helpful!

---

### Post by Ek0nomik on 2007-07-31
What are you trying to change the file permissions of?

You could change the permissions via the terminal.  If you want to make a file or folder part of your username and group;

```
sudo chown *username*:*usergroup* *foldername*
```

So as an example, in my case, I might make it;

```
sudo chown dove:dove ~/Downloads
```

This would make my Downloads folder in my home directory belong to the user dove, and the usergroup dove.

---

### Post by Hughsy on 2007-07-31
Hmm, seems I dont have permission to do that:

```
chown: changing ownership of `/media/host': Operation not permitted

```

Strange. I should probably mention that I installed Ubuntu using wubi, if that somehow affects permissions.

---

### Post by Ek0nomik on 2007-07-31
> **Hughsy said:**
> Hmm, seems I dont have permission to do that:

```
chown: changing ownership of `/media/host': Operation not permitted

```

Strange. I should probably mention that I installed Ubuntu using wubi, if that somehow affects permissions.

Did you use *sudo* at the front of your command?

---

### Post by Hughsy on 2007-07-31
I did indeed. I leave it for tonight and tinker around with it again tomorrow. thanks for your time and help though.

---

### Post by Ek0nomik on 2007-07-31
> **Hughsy said:**
> I did indeed. I leave it for tonight and tinker around with it again tomorrow. thanks for your time and help though.

I would try using 'su' then.

```
su
```

Then you should get a password prompt where you type in your root password.

Run the command I listed earlier, than close out that terminal and create a new one.  (You don't want to mess around as root for normal activity.)

No problem.  I like helping.  :)

---

### Post by Hughsy on 2007-08-01
Hi, back again. I tried using su instead of sudo, still no luck. Attached is a screenshot of what happens when I tried writing to the drive. Obviously its frustrating as I have large video files I'd like to transfer!

---

### Post by Ek0nomik on 2007-08-01
> **Hughsy said:**
> Hi, back again. I tried using su instead of sudo, still no luck. Attached is a screenshot of what happens when I tried writing to the drive. Obviously its frustrating as I have large video files I'd like to transfer!

Heh, you gotta love the spread of free videos, eh?  ;)

What is /media/host/?  An external hard drive?

If so, can you post the outputs of:

```
sudo fdisk -l
```

```
sudo mount
```

```
cat /etc/fstab
```

**Edit**:  According to your picture, it isn't /media/host, it's /media/disk-1.  Just pointing that out...

Also, unless you are running Windows, I don't think the Dell Backup partitions are worthwhile.  Unless the Dell you bought came with Ubuntu installed and they have some sort of backup utility for Ubuntu.  (Just thought I'd point that out in case you wanted to free up some space)

---

### Post by Hughsy on 2007-08-01
Hey again, these are the results for the commands: 

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       22386   179759317+   7  HPFS/NTFS
/dev/sda3           22387       29982    61014870    f  W95 Ext'd (LBA)
/dev/sda4           29983       30393     3301357+  db  CP/M / CTOS / ...
/dev/sda5           22387       29982    61014838+   b  W95 FAT32

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2       30515   245103705    f  W95 Ext'd (LBA)
/dev/sdb5               2       30122   241946901    7  HPFS/NTFS

```

```

hugh@Home:~$ sudo mount
/media/host/wubi/disks/system.virtual.disk on / type ext3 (rw,sync)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/media/host/wubi/disks/home.virtual.disk on /home type ext3 (rw,sync,loop=/dev/loop1)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda4 on /media/DellRestore type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sda2 on /media/disk type ntfs (rw,nosuid,nodev,umask=222,utf8)
/dev/sdb5 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)

```

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults          0   0
/media/host/wubi/disks/system.virtual.disk      /               ext3        loop,sync         0   1
/media/host/wubi/disks/home.virtual.disk      /home           ext3        loop,sync         0   2
/media/host/wubi/disks/swap.virtual.disk      none            swap        sw                0   0

```

Also I know what you mean about the dell paritions. Ive been meaning to get rid of them. If anything goes wrong I usually format and resintall from scratch. 
The drives are both external and internal.

---

### Post by Ek0nomik on 2007-08-01
Ok, I must admit I don't know much about Wubi.  You use Wubi to install Ubuntu through Windows if I am not mistaken?  I have no idea why there is a /media/host/wubi/ to be honest.  If you say you do a format/reinstall from scratch, why would you use Wubi?

Anyways, you are trying to put data onto disk-1, correct?

```
/dev/sdb5 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)
```

This tells us that disk-1 is an NTFS [filesystem]("http://en.wikipedia.org/wiki/Filesystems#File_systems_and_operating_systems").

NTFS filesystems won't work out of the box in Linux.  You need to install support so you can read and write to the hard drive.  

Here are some links that you may find worthwhile to read on adding support:

[https://wiki.ubuntu.com/ntfs-3g](https://wiki.ubuntu.com/ntfs-3g)

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I at one point installed NTFS-3G and used it for about a day with my NTFS hard drive.  However, I use Linux almost exclusively at home, so I formatted my hard drive to FAT32.  This way, the hard drive has both reading and writing capabilities on any Linux platform, and it can be mounted automatically.  I could also plug it into a Windows machine and the latter applies to it.  It's a good way to be universal with the hard drive.

A lot of people do use NTFS-3G though on these forums and seem to like it, so maybe you will too.

As always, if you have a question or comment feel free to reply or send me a private message.  I'm at work right now, and I am bored out of my mind.  :)

**Edit**:  You seem to have a lot of partitions.  Why do you have so many?  You have one external hard drive and one internal hard drive it looks like, right?  Is there any reason why you have them split up so much?

---

### Post by Hughsy on 2007-08-01
I used wubi as it was a quick and painless way to install ubuntu. I have two external harddrives and this is a (relatively) new Dell PC which comes with an inordinate amount of partitions, which I havent got around to removing. 

I'll give those links a go, but if Im not mistaken, NTFS is a proprietary filesystem which is unstable to read and write to in Linux. I'll tread carefully.

There shouldnt be any issue with the FAT32 partitions though?

---

### Post by Hughsy on 2007-08-01
Just thought I'd post that my NTFS external drive is now read/write-able :)

---

### Post by Ek0nomik on 2007-08-02
> **Hughsy said:**
> Just thought I'd post that my NTFS external drive is now read/write-able :)

Excellent!  What about your permission issues?  That still needs to be resolved, yes?  Or has that been solved as well?

---

### Post by Hughsy on 2007-08-02
permission issues still giving me trouble, but at least I have full access to my library of files

---

### Post by Ek0nomik on 2007-08-03
> **Hughsy said:**
> permission issues still giving me trouble, but at least I have full access to my library of files

Hughsy:  Try unmounting your NTFS partition, then mount it again, but without 'sudo' in front of it.  This way it gets mounted with your user permissions.  I think should solve the issue.

---

