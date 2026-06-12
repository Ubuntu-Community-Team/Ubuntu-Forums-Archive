---
title: "An Amalgam."
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by domat00 on 2007-06-14
Hi!  This is my first post in a Linux-related forum, and I'm hoping I might be able to resolve a few more problematic discrepancies I've been having on my ever delightful journey with Feisty!

First off, I just want to say that I love Linux - the feel, the look, the speed.  It's fantastic.  I migrated from XP Home, and with a little bit of Google, I've been basically able to get what I want working perfectly for my hardware, save for my printer.  But that's for later.  

Anyways, I have 4 issues:

1.)  I'm a complete Linux-illiterate!  I can't for the life of me role through these problems on my own, though I've tried.  But I'm a very good at taking orders!  I'm adept at using console, as long as I either know what commands to use or am told what to input - lol.

2.)  I use a 150GB WD Raptor for my OS's, and a 250GB WD Caviar for storage.  So far I've come to the conclusion that I can drop Windows completely, save for a few support issues that I'm having.  But specific to this issue, I cannot configure my 250GB drive to ext3, without installing Ubuntu on it to begin with, which I am desperate to avoid.  Right now I have my Raptor divided in two, Windows on one partition, and Ubuntu on the other.  If I could get a folder of my files off of the Windows partition and transfered from that disk onto the Caviar, then I could do away with the Windows partition, and concentrate on Ubuntu.

3.)  This isn't directly related to Ubuntu, but I'm hoping that someone out there might be sympathetic and can help me through this particular struggle:  patching Wine.  Right now, all I need to do to break my dependency on Windows is, is to set up Call of Duty 2 in Linux.  All of the programs that I need to use with it are supported by Linux, so now the only chore is getting Call of Duty installed, which presents the problem:  Wine apparently doesn't support Call of Duty 2 out-of-the-box, and I have absolutely no idea how to apply the patch that would solve my problem!  So that is where you, my fellow Ubuntu-ers come in.  I humbly request your assistance!  lol

4.)  And finally, I own a Lexmark X6170-series All-in-One, but Ubuntu doesn't natively support the correct driver (the driver that it auto-detects when adding a new printer via the GUI is wrong, and a test page does not print with a variety of drivers that I have attempted), and Lexmark themselves does not have a Linux driver for Ubuntu (SuSe and TurboLinux [Hungarian only]), so that is a dead end.  I have not Googled to see if there is a driver for it, and, being a n00b to Linux, I don't think I would succeed in the undertaking to create my own driver.  lol

So there it is, my friends.  I'm hoping that with all of the worlds greatest open-source coders out there, perhaps one or two might be able to shed some light into my dimly-lit Feisty-filled world!  Thanks in advance, and I hope this is coherent!  :)

---

### Post by Nikron on 2007-06-14
If there's nothing on the Caviar drive you can simply do mkfs.ext3 on it when it's unmounted.  For example, I would think the Caviar partition would be called /dev/sdb1, so you would simply do

```

sudo mkfs.ext3 /dev/sdb1

```

But be careful, you can easily wipe out all your data.  It's happened to me.  (Another option would be to run the command "fdisk" as root which gives a command line environment to control your disks when their unmounted.  However the commands while running it are a tad cryptic, so I wouldn't recommend it.  Plus, you'd probably have to do it from a livecd of some sort.)

---

### Post by domat00 on 2007-06-14
The Caviar is completely empty:  the Raptor has everything on it:  I need to format the Caviar and be able to transfer a folder to it, and then I can just get rid of my Windows partition on the Raptor.  Right now I'm going to get rid of everything I didn't have when I installed Linux (i.e. restore factory defaults  hehehehe).

Also, the Caviar is named /dev/disk.  I apparently don't have the permissions to rename it to what it should be.  (!)

---

### Post by Bachstelze on 2007-06-14
1. To learn more about the terminal : [http://linuxcommand.org/](http://linuxcommand.org/)

2. You can use fdisk or mkfs as was posted above. If you like a GUI, GParted is nice too.

3. We have a section of the forum dedidacted to gaming, you might have better luck there.

4. Sadly, Lexmark printers are a no-go at the moment, and that's not likely to change any time soon. Get a nice HP printer ;)

---

### Post by domat00 on 2007-06-14
I'm sad to say I cannot locate GParted, though it does look as if it is installed in Synaptic.  Where can I run it from?  I've just been using Gnome Partition Editor which I installed through Add/Remove Programs.

---

### Post by Bachstelze on 2007-06-14
**G**nome **Part**ition **Ed**itor = GParted ;)

---

### Post by domat00 on 2007-06-14
Well ain't that the pickler.  That's what I tried to use and now I can't access the disk whatsoever.

---

### Post by Nikron on 2007-06-14
You have to mount the disk.  If your disk is called 'disk', you can mount it by doing ```

mkdir /the/place/you/want/to/mount/it/at/ (ie /mnt/disk/)
sudo mount /dev/disk /mnt/disk/

```

Then navigate to /dev/disk/(You wont have write permissions, but you should probably have read permissions).   Then you have to decided what you want this disk to permantely be.  Home perhaps?  If so you'd mount the disk, copy your home directory to your disk, remove the the home directory from your 150 disk, and edit fstab to mount the Caviar as home.  An example of this would be 
```

sudo cp -R /home /mnt/disk/
sudo echo "/dev/disk /home ext3 defaults 0 1" >> /etc/fstab

```

Don't copy paste my code, it's only an example, I'm not sure it would work right on your computer

---

### Post by domat00 on 2007-06-14
No, no, all I am trying to do is format the Caviar correctly so I can write to it.  I don't wish to have part of the OS on a seperate disk.  I want to use the disk that Linux is on currently as the OS disk with the programs and apps and games and such, and use the Caviar as a storage medium.  I don't know if that's getting across.  But this brings me back to another issue:  How can I set myself as the owner so I can actually do what I need to do?  How do I assign myself as root or owner or whatever?  Half the time I need to do something I come up with an error that says I have insufficient privileges to copy something.

---

### Post by Nikron on 2007-06-14
> **domat00 said:**
> No, no, all I am trying to do is format the Caviar correctly so I can write to it.  I don't wish to have part of the OS on a seperate disk.  I want to use the disk that Linux is on currently as the OS disk with the programs and apps and games and such, and use the Caviar as a storage medium.  I don't know if that's getting across.  But this brings me back to another issue:  How can I set myself as the owner so I can actually do what I need to do?  How do I assign myself as root or owner or whatever?  Half the time I need to do something I come up with an error that says I have insufficient privileges to copy something.

What do you think the point of /home is?  It's where you point all your stuff.  Your disk is going to have to be part of the overall system _somehow_.  /mnt/whatever or /opt/  If you make it your home _then_ you will definately have write permissions to it.  Actually I would suggest mounting the disk as /home/yourusername/storage/ if you want to put only storage things on it.  Then the storage folder in your home would actually be the disk.  Right now, root probably owns the disk because gnome probably auto mounted it to /mnt/.  Would you mind posting the output of "sudo fdisk -l"

---

### Post by domat00 on 2007-06-14
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    5  Extended
/dev/sda5               1       30401   244195969+  83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9120    73256368+   7  HPFS/NTFS
/dev/sdb2            9121       17992    71264340   83  Linux
/dev/sdb3           17993       18241     2000092+  82  Linux swap / Solaris

Sorry, I can be bull-headed, so just prod me a bit.

---

### Post by Bachstelze on 2007-06-14
So, what's the problem ?

```
mount -t ext3 /dev/sda5 /somewhere
```

You're there !

---

### Post by Nikron on 2007-06-14
> **domat00 said:**
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    5  Extended
/dev/sda5               1       30401   244195969+  83  Lin
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9120    73256368+   7  HPFS/NTFS
/dev/sdb2            9121       17992    71264340   83  Linux
/dev/sdb3           17993       18241     2000092+  82  Linux swap / Solaris

Sorry, I can be bull-headed, so just prod me a bit.

I'm trying to explain to you want you should do rather than just telling you to do it.  Me just telling you to randomly paste commands would be pointless in the long run.  Anyway, it looks like /dev/sda is your 250GB storage device.  Honestly, I'm not familiar why it's split up the way it is.  What I would do is is type in "gparted" and run through that program making sure that /dev/sda becomes formated as one gigantic ext3 partition, since that's what you want.  Before you do that do "sudo umount /dev/sda5" and do the same for sda1. 

Sorry if I'm being a confusing.


Edit: scratch the fdisk thing.

Man, I can't understand how your Caviar is partitioned right now..  Does it just have a linux partion sitting in the middle of it with nothing at begining or what?

---

### Post by domat00 on 2007-06-14
> **HymnToLife said:**
> So, what's the problem ?

```
mount -t ext3 /dev/sda5 /somewhere
```

You're there !

That didn't do anything, and I tried to sudo the code after the first attempt came back with a "only root can do that" error.

---

### Post by domat00 on 2007-06-14
> **Nikron said:**
> I'm trying to explain to you want you should do rather than just telling you to do it.  Me just telling you to randomly paste commands would be pointless in the long run.  Anyway, it looks like /dev/sda is your 250GB storage device.  Honestly, I'm not familiar why it's split up the way it is.  What I would do is is type in "gparted" and run through that program making sure that /dev/sda becomes formated as one gigantic ext3 partition, since that's what you want.  Before you do that do "sudo umount /dev/sda5" and do the same for sda1. (Or, if you want to stick to the terminal you can do "sudo fdisk /dev/sda" after /dev/sda5 and /dev/sda1 is unmounted, then hit 'm' for help.)

Sorry if I'm being a confusing.

Not at all, it was very concise.  I'm using the terminal this time to try and bypass the permissions problem, and I've come across a value I'm not sure I need to choose:  I have an idea, but that was just trial and error.  It give me an option for an extended partition or a primary partition.  Which should I choose?

---

### Post by deadlikeoscar on 2007-06-14
You could just format the drive to NTFS or if it is leave it that way. Pull that Windows folder off of your Raptor drive and onto the Caviar. Now you can get rid of Windows on the Raptor. When Ubuntu is up and running on the Raptor use Synaptic to get ntfs-config. This will setup your NTFS drive(Caviar) with read/write. You will just mount the drive under ntfs-config as /caviar or whatever you want to name it. It will appear as a drive on your desktop and you can do whatever you want to with the drive. It works really well and you don't have to switch to a different filesystem.

---

### Post by domat00 on 2007-06-14
That's the thing:  it won't allow me to format that disc to NTFS through the livecd (GParted doesn't support NTFS partition creation) without completely installing Ubuntu, and that's what I'm trying to avoid.

---

### Post by Bachstelze on 2007-06-14
> **domat00 said:**
> That didn't do anything, and I tried to sudo the code after the first attempt came back with a "only root can do that" error.

It's normal that it outputs nothing, what should it output ? You should now be able to browse the disk contents.

---

### Post by Nikron on 2007-06-14
Don't run anaconda, the installer of Ubuntu run gparted a partition tool.  If you are having trouble with the livecd, burn off a copy of the real thing [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/).

---

### Post by deadlikeoscar on 2007-06-14
I figured you could have done that through Windows but maybe that wasn't an option.

---

### Post by domat00 on 2007-06-14
> **HymnToLife said:**
> It's normal that it outputs nothing, what should it output ? You should now be able to browse the disk contents.

That's how I know it did nothing:  I looked in my folders and nothing changed.  I tried accessing the disc but it still came back with an insufficient privileges error.

---

### Post by domat00 on 2007-06-14
> **Nikron said:**
> Don't run anaconda, the installer of Ubuntu run gparted a partition tool.  If you are having trouble with the livecd, burn off a copy of the real thing [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/).

I tried GParted but that's what came up with funky disc names and the insufficient privileges error.

---

### Post by domat00 on 2007-06-14
> **deadlikeoscar said:**
> I figured you could have done that through Windows but maybe that wasn't an option.

My Windows partition is inaccessable.  I layed waste to the GRUB boot menu with an impromptu installation of 64-bit Feisty.

---

### Post by deadlikeoscar on 2007-06-14
I'm sure you can fix the GRUB situation but since that is the case I would suggest to keep going on the path you are already on then.;)

---

### Post by Bachstelze on 2007-06-14
> **domat00 said:**
> That's how I know it did nothing:  I looked in my folders and nothing changed.  I tried accessing the disc but it still came back with an insufficient privileges error.

Oh, really ? Just type *mount* and paste what you get.

---

### Post by domat00 on 2007-06-14
/dev/sdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
tmpfs on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw,mode=0755)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=aaron)

---

### Post by Bachstelze on 2007-06-14
Well, if you typed *exactly* what I told you, it will not work indeed. You must replace /somewhere with where you want your partition mounted ;)

---

### Post by Nikron on 2007-06-14
And note, that /somewhere must be a place where your user has write permissions to.  Otherwise you'll get the permissions problem again.

---

### Post by domat00 on 2007-06-14
> **HymnToLife said:**
> Well, if you typed *exactly* what I told you, it will not work indeed. You must replace /somewhere with where you want your partition mounted ;)

I did...  I typed mount -t ext3 /dev/sda5/home/aaron/storage and when nothing changed I then sudo'd it.  Do I need to change the /storage to an existing directory?  That doesn't seem right to me...

---

### Post by Bachstelze on 2007-06-14
The mount point (i.e. the directory you want to mount the partition too) *must* exist !

---

### Post by domat00 on 2007-06-14
...  Wish I would have known that  LOL.

OK, I mounted the drive with sudo mount -t ext3 /dev/sda5/home/aaron/Storage, and I hit Properties on Storage and it gave me Free Space as 24GB's.

?

I need the full 250GB.

---

### Post by Nikron on 2007-06-14
> **domat00 said:**
> ...  Wish I would have known that  LOL.

OK, I mounted the drive with sudo mount -t ext3 /dev/sda5/home/aaron/Storage, and I hit Properties on Storage and it gave me Free Space as 24GB's.  ?  I need the full 250GB.

It's because you have incorrectly partitioned your /dev/sda as your fdisk shows.  Like I tried to tell you before =P.  You need to partition it _somehow_ gparted, mkfs, or _anything_ and partition the whole thing.

Once again, I'd recommend gparted.

---

### Post by domat00 on 2007-06-14
Well I'd need a step-by-step through it, because last time I got the whole no priviliges thingy...

EDIT:  I tried creating a Primary partition with GParted and I got an error while formatting, and did a dmesg | tail and got this:

[  216.594408] end_request: I/O error, dev fd0, sector 0
[  216.618624] end_request: I/O error, dev fd0, sector 0
[ 9381.460105] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9381.476687] ISOFS: changing to secondary root
[ 9551.718888] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 9551.757245] ISO 9660 Extensions: RRIP_1991A
[11815.016934] ISO 9660 Extensions: Microsoft Joliet Level 3
[11815.082847] ISO 9660 Extensions: RRIP_1991A
[14745.592011] EXT3-fs error (device sda1): ext3_check_descriptors: Block bitmap for group 880 not in group (block 0)!
[14745.592364] EXT3-fs: group descriptors corrupted!

So unless you know what I'm doing wrong in here, I think I'll steer clear of GParted.  :P

---

### Post by Nikron on 2007-06-14
Look at below post, sorry double post

---

### Post by Nikron on 2007-06-14
Alright

do it in this exact order

**This is assuming that /dev/sda is the 250GB device, and that the previous fdisk -l is still true.  Be very careful as this can *easily* erase all your data.**

sudo umount /dev/sda5
sudo umount /dev/sda1
sudo fdisk /dev/sda
hit 'd'
<enter>
hit 'd'
<enter>
hit 'n'
<enter>
hit 'p'
<enter>
hit '1'
<enter>
<enter>
<enter>
hit 'w'
<enter>
sudo mkfs.ext3 /dev/sda1
sudo mount /dev/sda1 /home/aaron/Storage

Edit: it gave that error because you didn't umount your drives..

---

### Post by domat00 on 2007-06-14
sudo mkfs.ext3 /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

That's what I got.

---

### Post by Nikron on 2007-06-14
> **domat00 said:**
> sudo mkfs.ext3 /dev/sda1
mke2fs 1.40-WIP (14-Nov-2006)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

That's what I got.

Can you post what your 'sudo fdisk -l' is now?   Probably you /dev/sda has no partitions now, and you need to format it.

---

### Post by domat00 on 2007-06-14
I tried that but it no longer out-puts.  Lemme know if I need to re-enter GParted.  :P

EDIT:  Ack, sorry.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    5  Extended
/dev/sda5               1       30401   244195969+  83  Linux

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9120    73256368+   7  HPFS/NTFS
/dev/sdb2            9121       17992    71264340   83  Linux
/dev/sdb3           17993       18241     2000092+  82  Linux swap / Solaris

---

### Post by Nikron on 2007-06-14
Actually, entering gparted the first time may have completely screwd up your system since you tried to format an unmounted drive.   I'd suggest trying to boot into Windows to see if that's still alive.  Chances are that you may have reinstall Ubuntu (Hope you make backups, forgot to mention th at earlier, sorry).  Also, I need to get to bed, so hopefully someone will come and help you, doesn't look like I'm doing a very good job of it.:(

---

### Post by domat00 on 2007-06-14
> **Nikron said:**
> Actually, entering gparted the first time may have completely screwd up your system since you tried to format an unmounted drive.   I'd suggest trying to boot into Windows to see if that's still alive.  Chances are that you may have reinstall Ubuntu (Hope you make backups, forgot to mention th at earlier, sorry).  Also, I need to get to bed, so hopefully someone will come and help you, doesn't look like I'm doing a very good job of it.:(

No problem, I'll just have to wait.  And if I could get into Windows I wouldn't be having this problem.  lol  Anyways, thanks for wasting your time on me.  :p

---

### Post by domat00 on 2007-06-14
::Bump::

---

### Post by domat00 on 2007-06-14
Do you know of a tool I can download into Feisty that will allow me to creat an NTFS or ext3 partition and mount the disk as sda1?  The computer assigns it as /dev/sda, but so far my attempts to format and mount have been unsuccessful and riddled with insufficient privileges errors.  Any help would be greatly appreciated.

---

