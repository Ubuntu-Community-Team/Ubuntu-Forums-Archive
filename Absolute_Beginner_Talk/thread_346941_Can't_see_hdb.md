---
title: "Can't see hdb"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by kliljedahl on 2007-01-26
Here's the deal. I have 4 hard drives, hda = 80GB (ubuntu 6.1), hdb 120GB, sda 40GB,  sdb 120GB. I switched totally to ubuntu about 3 weeks ago and spent several days transferring all the data from disc to disc until all 3 were formatted ext3. Then about a week ago I had a bootup problem which I posted here:[URL="http://www.ubuntuforums.org/showthread.php?t=340747"]] Since I got no response I decided to do a fresh install on hda and everything is fine except hdb is not to be found. sda shows up as "usb disk", and sdb shows up as "usb disk-1". When I put in the live CD gparted sees it, but I can't do anything with it except format, which I don't want to do since it has data I need. How can I get it recognized? I've been searching the forums and have seen several semi-related threads, but none addressing my particular question. I'm at work now, so if there are specific questions I need to answer, those will have to remain unanswered until this evening. Thanks in advance for everyone's patient and kind help.

---

### Post by citizenofnowhere on 2007-01-26
Sounds like something bad happened to that hard disk (given your previous post).

Do you have any operating systems on it? 

If your livecd can see the harddisk try running a disk check from there:

e2fsck -ncfv /dev/hdb (this will tell you if there are any errors but is only a test run - it won't touch the hardidsk)

e2fsck -pcfv /dev/hdb should automatically fix those errors for you.

When I have problems with hard disks, I pop in a puppy livecd. Puppy is a tiny distro that isn't great for daily use, but because it fits on a thumbdrive it's great for debugging. It also mounts practically anything: [http://www.puppyos.com/](http://www.puppyos.com/) See if puppy can mount it, then use it to backup the data and format (easiest option by far if you have the space).

Post if you still have problems - we'll figure it out.

---

### Post by kliljedahl on 2007-01-26
No operating system.My only OS is 6.10 on hda. All I'm using the other three for is data and music storage. Unfortunately hdb has all the My Documents files from when I was running XP.
Does it need mounting? I didn't see that option in gparted,only unmount.

---

### Post by taurus on 2007-01-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by citizenofnowhere on 2007-01-26
Yep, you'll need to make a directory for it, for instance

```

sudo mkdir /mnt/files
sudo mount /dev/hdb /mnt/files

```

Sounds like it's already mounted though if the only option in gparted is to unmount... Have you tried the puppy option?

---

### Post by taurus on 2007-01-26
Well, you can check to see if it's already mounted with

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by kliljedahl on 2007-01-26
> **citizenofnowhere said:**
> Yep, you'll need to make a directory for it, for instance

```

sudo mkdir /mnt/files
sudo mount /dev/hdb /mnt/files

```

Sounds like it's already mounted though if the only option in gparted is to unmount... Have you tried the puppy option?

No I haven't, I'm still at work. I'll have a whole weekend to try to figure it out. I see unmount in gparted, but it's not highlighted so not an option. I don't see mount anywhere.

---

### Post by kliljedahl on 2007-01-26
I'm home now, tried bith suggestions. ihis is the result:

~$ e2fsck -ncfv /dev/hdb
e2fsck 1.39 (29-May-2006)
e2fsck: Permission denied while trying to open /dev/hdb
You must have r/w access to the filesystem or be root
kliljedahl@kliljedahl-desktop:~$ sudo mkdir /mnt/files
Password:
kliljedahl@kliljedahl-desktop:~$ sudo mount /dev/hdb /mnt/files
mount: you must specify the filesystem type
kliljedahl@kliljedahl-desktop:~$

---

### Post by citizenofnowhere on 2007-01-26
Sorry, you need to be sudo to check the file system.

Try give it

```
sudo mount -t ext3 /dev/hdb
```

-t specifies the filesystem type (ext3, vfat, etc).

---

### Post by kliljedahl on 2007-01-26
> **taurus said:**
> Well, you can check to see if it's already mounted with

Applications -> Accessories -> Terminal
```
df -h
```

Did that, got this: 
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G  5.5G   62G   9% /
varrun                502M  132K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  180K  9.9M   2% /proc/bus/usb
udev                   10M  180K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  485M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              38G  177M   36G   1% /media/usbdisk
/dev/sdb1             113G   79G   29G  74% /media/usbdisk-1
/dev/hdb1             111G   29G   76G  28% /mnt/files

---

### Post by kliljedahl on 2007-01-26
> **citizenofnowhere said:**
> Sounds like something bad happened to that hard disk (given your previous post).

Do you have any operating systems on it? 

If your livecd can see the harddisk try running a disk check from there:

e2fsck -ncfv /dev/hdb (this will tell you if there are any errors but is only a test run - it won't touch the hardidsk)

e2fsck -pcfv /dev/hdb should automatically fix those errors for you.

When I have problems with hard disks, I pop in a puppy livecd. Puppy is a tiny distro that isn't great for daily use, but because it fits on a thumbdrive it's great for debugging. It also mounts practically anything: [http://www.puppyos.com/](http://www.puppyos.com/) See if puppy can mount it, then use it to backup the data and format (easiest option by far if you have the space).

Post if you still have problems - we'll figure it out.

Tried that, got this:
kliljedahl@kliljedahl-desktop:~$ e2fsck -pcfv /dev/hdb 
e2fsck: Permission denied while trying to open /dev/hdb
You must have r/w access to the filesystem or be root
kliljedahl@kliljedahl-desktop:~$ sudo e2fsck -pcfv /dev/hdb 
Password:
e2fsck: Bad magic number in super-block while trying to open /dev/hdb
/dev/hdb: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

kliljedahl@kliljedahl-desktop:~$

---

### Post by kliljedahl on 2007-01-27
So what thr heck is "Bad magic number in super-block"? I thought this was technology, not magic. Looks like something is really screwed up.

---

### Post by citizenofnowhere on 2007-01-27
Here are a couple of threads I dug up with Google. They're a bit on the heavy side, but it sounds like something fried a block on your harddisk. Could have been a number of things - overheating, power surge.. doesn't sound OS specific.

[http://linuxgazette.net/issue32/tag_superblock.html](http://linuxgazette.net/issue32/tag_superblock.html)

Try google for the error and you'll find a lot of posts about it. I;m pretty sure you'll be able to find something on Ubuntu forums as well. 

If it's a removable drive (and I know this might sound counter-intuitive at first since you've just wiped windows) - plug it into a Windows machine and see if it boots up. The thread suggests that if you have norton dos tools lying around even better - might be a bit more user friendly than those command line fixes. 

Just MUCH longer :)

---

### Post by kliljedahl on 2007-01-27
Got this when I tried to reboot, saved in /var/log/fsck/checkfs: 

Log of fsck -C -R -A -a 
Sat Jan 27 08:31:01 2007

fsck 1.39 (29-May-2006)
fsck.ext3: No such file or directory while trying to open /devhdb1

/devhdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Sat Jan 27 08:31:01 2007

---

### Post by kliljedahl on 2007-01-27
Also get this when rebooting:
a maintenance shell will now be started
bash: no job control in this shell
bash: groups:command not found
bash:lesspipe:command not found
bash: dircolors:command not found

---

### Post by kliljedahl on 2007-01-27
Ok, just did a fresh install on hda and no longer get the error message when I reboot, although I still can't access hdb . I suspected I'd confused the system by entering too many terminal commands. The error message was due to me and my newness. There were so many suggestions and I tried them all, I'm sure there were conflicting commands somewhere.

---

### Post by kliljedahl on 2007-01-27
> **citizenofnowhere said:**
> Yep, you'll need to make a directory for it, for instance

```

sudo mkdir /mnt/files
sudo mount /dev/hdb /mnt/files

```

Sounds like it's already mounted though if the only option in gparted is to unmount... Have you tried the puppy option?

Back after a fresh install, got this: 
 sudo mkdir /mnt/files
Password:
kliljedahl@kliljedahl-desktop:~$ sudo mount /dev/hdb /mnt/files
mount: you must specify the filesystem type
kliljedahl@kliljedahl-desktop:~$ 

It's just the "My Documents" file from XP. Conglomeration of many types of files. ](*,) ](*,) ](*,) ](*,)

---

### Post by taurus on 2007-01-27
```
sudo mount -t ntfs /dev/hdb1 /mnt/files
-or- 
sudo fdisk -l
```

---

### Post by kliljedahl on 2007-01-28
This is what I got: sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631   83  Linux

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14946   120053713+  83  Linux
kliljedahl@kliljedahl-desktop:~$ 

but I still can't see it

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Well, you can check to see if it's already mounted with

Applications -> Accessories -> Terminal
```
df -h
```

Apparently it's not mounted: 
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G  5.2G   62G   8% /
varrun                502M  132K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  180K  9.9M   2% /proc/bus/usb
udev                   10M  180K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  485M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              38G  177M   36G   1% /media/usbdisk
/dev/sdb1             113G   79G   29G  74% /media/usbdisk-1
kliljedahl@kliljedahl-desktop:~$

---

### Post by taurus on 2007-01-28
```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> ```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```

This is getting frustrating, says it's mounted but I still can't see it. Here's the result:

/dev/hdb1 already mounted or /media/hdb1 busy
mount: according to mtab, /dev/hdb1 is already mounted on /media/hdb1
kliljedahl@kliljedahl-desktop:~$ df -h

---

### Post by taurus on 2007-01-28
There is no output when you run that last command!

```
df -h
```
How about

```
mount
```

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> ```
sudo mkdir /media/hdb1
sudo mount -t ext3 /dev/hdb1 /media/hdb1
df -h
```

This is getting frustrating, says it's mounted but I still can't see it. Here's the result:

/dev/hdb1 already mounted or /media/hdb1 busy
mount: according to mtab, /dev/hdb1 is already mounted on /media/hdb1
kliljedahl@kliljedahl-desktop:~$ df -h
[IMG]http://i38.photobucket.com/albums/e121/kliljedahl/MySpace/Screenshot-1.png[/IMG]

---

### Post by taurus on 2007-01-28
Can you just minimize all your windows and see if there is an icon on the desktop for /media/hdb1?

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> There is no output when you run that last command!

```
df -h
```
How about

```
mount
```

Then I get:
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              71G  5.2G   62G   8% /
varrun                502M  132K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb             10M  180K  9.9M   2% /proc/bus/usb
udev                   10M  180K  9.9M   2% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   18M  485M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/sda1              38G  177M   36G   1% /media/usbdisk
/dev/sdb1             113G   79G   29G  74% /media/usbdisk-1
kliljedahl@kliljedahl-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type ext3 (rw,nosuid,nodev)
/dev/sdb1 on /media/usbdisk-1 type ext3 (rw,nosuid,nodev)
kliljedahl@kliljedahl-desktop:~$

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Can you just minimize all your windows and see if there is an icon on the desktop for /media/hdb1?

Not showing there, just the two externals. I've even re-booted twice, just in case:

[IMG]http://i38.photobucket.com/albums/e121/kliljedahl/MySpace/Screenshot-2.png[/IMG]

---

### Post by taurus on 2007-01-28
Everytime you reboot, you need to mount the drive again since you mounted it by hand.  If you don't want to mount it each time you boot, then you need to add an entry in /etc/fstab to mount it automatically upon boot.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Everytime you reboot, you need to mount the drive again since you mounted it by hand.  If you don't want to mount it each time you boot, then you need to add an entry in /etc/fstab to mount it automatically upon boot.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

OK, installed gparted, says it's not mounted. Is it, or isn't it? I'm determined to learn this people, Thanks once again for your incredible patience: 

[IMG]http://i38.photobucket.com/albums/e121/kliljedahl/MySpace/Screenshot-3.png[/IMG]

---

### Post by taurus on 2007-01-28
Output of these, please.

```
sudo fdisk -l
mount
```

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Output of these, please.

```
sudo fdisk -l
mount
```

Here ya' go: 

kliljedahl@kliljedahl-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9355    75144006   83  Linux
/dev/hda2            9356        9729     3004155    5  Extended
/dev/hda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   83  Linux

Disk /dev/sda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5005    40202631   83  Linux

Disk /dev/sdb: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14946   120053713+  83  Linux
kliljedahl@kliljedahl-desktop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sda1 on /media/usbdisk type ext3 (rw,nosuid,nodev)
/dev/sdb1 on /media/usbdisk-1 type ext3 (rw,nosuid,nodev)
/dev/hdb1 on /media/hdb1 type ext3 (rw)
kliljedahl@kliljedahl-desktop:~$

---

### Post by taurus on 2007-01-28
Your /dev/hdb1 is already mounted to /media/hdb1.

```
/dev/hdb1 on /media/hdb1 type ext3 (rw)
```
What happens when you run this from a terminal?

```
ls -la /media/hdb1
```

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Your /dev/hdb1 is already mounted to /media/hdb1.

```
/dev/hdb1 on /media/hdb1 type ext3 (rw)
```
What happens when you run this from a terminal?

```
ls -la /media/hdb1
```

Get this, which is what's there:  ls -la /media/hdb1
total 24
drwxr-xr-x  6 kliljedahl kliljedahl 4096 2007-01-18 05:43 .
drwxr-xr-x  8 root       root       4096 2007-01-28 15:04 ..
drwxr-xr-x 13 kliljedahl kliljedahl 4096 2006-12-25 18:03 My Documents
drwxr-xr-x 13 kliljedahl kliljedahl 4096 2007-01-11 18:21 My Documents 01-11-07
drwxr-xr-x 25 kliljedahl kliljedahl 4096 2006-11-07 06:10 My Photos
drwx------  2 kliljedahl kliljedahl 4096 2007-01-18 05:46 .Trash-kliljedahl
kliljedahl@kliljedahl-desktop:~$ 

Somehow I think I'm closer to being able to access it..

---

### Post by taurus on 2007-01-28
> **kliljedahl said:**
> Get this, which is what's there:  ls -la /media/hdb1
total 24
drwxr-xr-x  6 kliljedahl kliljedahl 4096 2007-01-18 05:43 .
drwxr-xr-x  8 root       root       4096 2007-01-28 15:04 ..
drwxr-xr-x 13 kliljedahl kliljedahl 4096 2006-12-25 18:03 My Documents
drwxr-xr-x 13 kliljedahl kliljedahl 4096 2007-01-11 18:21 My Documents 01-11-07
drwxr-xr-x 25 kliljedahl kliljedahl 4096 2006-11-07 06:10 My Photos
drwx------  2 kliljedahl kliljedahl 4096 2007-01-18 05:46 .Trash-kliljedahl
kliljedahl@kliljedahl-desktop:~$ 

Somehow I think I'm closer to being able to access it..

Those are the directories on /dev/hdb1.  You can navigate to those directories (or folders if you want to call them that) with nautilus or

```
cd "/media/hdb1/My Documents"
ls -la
```

---

### Post by kliljedahl on 2007-01-28
> **taurus said:**
> Those are the directories on /dev/hdb1.  You can navigate to those directories (or folders if you want to call them that) with nautilus or

```
cd "/media/hdb1/My Documents"
ls -la
```

Ok thanks for that, I saved the codes, thank you. But why doesn't it appear as one of my hard drives? I know the data was not gone, just inaccessible, (more than likely an error somewhere on my part). I hate being a newbie at anything, but I will learn this.

---

### Post by kliljedahl on 2007-01-28
Crap, it only worked that once. now it only shows the hda files. Why did it only work once?

---

### Post by taurus on 2007-01-28
Because you mounted it from a terminal.  When you reboot, you have to mount it again unless you add an entry in /etc/fstab for it.  Then, it will be mounted each time you boot Ubuntu.

```
/dev/hdb1   /media/hdb1  ext3   defaults   0   1
```

---

### Post by kliljedahl on 2007-01-28
Ok, I'm trying to learn as quickly as possible so I can quit asking stupid questions. how do I add it to /etc/fstab?

---

### Post by taurus on 2007-01-28
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```

---

### Post by kliljedahl on 2007-01-29
Thank you so very much for your help and patience, I can see it now. I wasn't aware of gksudo. I was trying sudo gedit and getting nowhere. I see I have very much more to learn.

---

### Post by taurus on 2007-01-29
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

