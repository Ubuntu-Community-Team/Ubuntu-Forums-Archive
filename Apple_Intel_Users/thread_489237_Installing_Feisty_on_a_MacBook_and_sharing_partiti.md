---
title: "Installing Feisty on a MacBook and sharing partitions"
date: 2007-07-01
forum: Apple Intel Users
---

### Post by darkmaster on 2007-07-01
Well, I'm going now to install Feisty on my macbook. It is the latest macbook version, black one. 

I installed it before on a MacMini and everything went fine except for sharing files between OSX and Linux. Now, I have a few questions before I proceed. These questions will actually change my installation method.

1) Can I use a different partition method than Bootcamp? With this tool, if I try to resize the disk, I can only create a disk as small as 40 gigs for Ubuntu. i don't like it. I whant to give OSX only a little disk left. How can I do it?

2) If I install Ubuntu carelessly, I'll surely be unable to read/write the OSX partition. Even following various guides I found to mount OSX partition, I always found that I cannot read the OSX partition unless I'm root. There was something to set with usernames and so on but when I tryed to change username in OSX the system got screwed up so I had to reinstall everything. Now I'm going to use a new mac and will have the opportunity to create a new user and everything new.
Will I be able to set a shortname or something? What should I set in OSX and Ubuntu to let the hard disk of OSX be written and read by Ubuntu? That's the real problem. The initial settings I think will be crucial. Any suggestion? I really need help on this step. 
A guide, someone who already tryed it, enything working for sure will do. 

Now I can tell you the guides I found around and will be refering to:

[http://ubuntuforums.org/showthread.php?t=480246&highlight=guide+macbook](http://ubuntuforums.org/showthread.php?t=480246&highlight=guide+macbook)
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[http://ubuntuforums.org/showthread.php?t=486483](http://ubuntuforums.org/showthread.php?t=486483) (I won't use this, too complicated and how do I partition all of this things on a mac? I can only use bootcamp... but I asked for a solution, so, maybe...)
[http://ubuntuforums.org/showthread.php?t=485579&highlight=guide+macbook](http://ubuntuforums.org/showthread.php?t=485579&highlight=guide+macbook)
[http://ubuntuforums.org/showthread.php?t=488885](http://ubuntuforums.org/showthread.php?t=488885)
[http://ubuntuforums.org/showthread.php?p=2943499#post2943499](http://ubuntuforums.org/showthread.php?p=2943499#post2943499)
[http://ubuntuforums.org/showthread.php?t=432335&highlight=macbook+how+to](http://ubuntuforums.org/showthread.php?t=432335&highlight=macbook+how+to)

---

### Post by grim1234 on 2007-07-01
1. For me the minimum size for the osx partition was 9gb, I'm not sure if the minimum is a % of your disk, this is with a 60gb disk on a macbook. Perhaps there's a method to shrink the osx partition after running bootcamp to set up the disk?

---

### Post by cyberdork33 on 2007-07-01
parted can partition guid disks.

As for mounting the OSX partition in Linux and getting permission errors, it is because OSX uses a similar file permissions system as linux. So, Ubuntu can read the permission set in OSX. Unfortunately, because it is a separate OS, the user and group ID numbers do not match, thus linux sees those files as owned by someone else. you can change the IDs to match as you can see in the various tutorials that you posted. Also if you want to write to the OSX volume then you need to make sure that journaling is turned off on the OSX side.

---

### Post by grim1234 on 2007-07-01
do you know how to create a hfsplus filesystem in linux?

---

### Post by cyberdork33 on 2007-07-01
you can suppossedly compile apple's tools in linux to use 'mkfs.hfs'

[http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools](http://gentoo-wiki.com/HOWTO_hfsplus#Compiling_Apple.27s_Filesystem_Tools)

---

### Post by darkmaster on 2007-07-04
> **cyberdork33 said:**
> parted can partition guid disks.

As for mounting the OSX partition in Linux and getting permission errors, it is because OSX uses a similar file permissions system as linux. So, Ubuntu can read the permission set in OSX. Unfortunately, because it is a separate OS, the user and group ID numbers do not match, thus linux sees those files as owned by someone else. you can change the IDs to match as you can see in the various tutorials that you posted. Also if you want to write to the OSX volume then you need to make sure that journaling is turned off on the OSX side.

Since I'm installing now a new Feisty, should I set my usrname to 501? Would this help? The real question is: is the username in OSX the shortname or the uid? My uid is 501, I saw it with netinfo. I think this is the real username I need to set in Ubuntu, am I correct? Do I have to set the same password too?

As for Bootcamp? Any way to partition is in a larger way? Where you suggesting I should use another tool to create partitions in OSX other than Bootcamp?

Is it the case for me to share a partition beetween OSX and Ubuntu? Which program do I use to create such a partition and which filesystem should I use?

---

### Post by cyberdork33 on 2007-07-04
I have used parted:
[http://ubuntuforums.org/showthread.php?t=89960](http://ubuntuforums.org/showthread.php?t=89960)

I *think* that the gparted live cd can handle hfsplus and guid partitioning now:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I have also used OSX's diskutil at the terminal. You can find information here:
[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

---

### Post by thully on 2007-07-04
Yes, you need to set your uid and gid (user id and group id) to 501.  You can do this with the usermod and groupmod tools - make sure you open a root shell (sudo su) before using.  You'll also need to chown / chgrp your entire home directory after changing your uid and gid (to reclaim ownership).

As for sharing filesystems, one can in fact share a home directory (search the archives for my recent thread on this).  However, you may have issues if you use the Unix tools often in OS X.  In any case, the filesystems you can use are:

* HFS+ (NON-journaled) This is just the standard OS X filesystem, you can turn off journaling in Disk Utility by selecting a partition, holding down Option and choosing the File menu - Disable Journaling will be there.  You can actually just share your OS X volume and use it for data if you use this for its filesystem.
* HFS+ (Case-sensitive, NON-jorunaled) (This is what you want if you're sharing the home directory, as it is case-sensitive like all Linux filesystems
* FAT32 This is simpler to work with - no permissions are involved, and FAT32 works in every OS you try it in.  You don't have to change the uid and gid of your user to access this.  However, it has limits due to being antiquated (no files over 4GB, most significantly), and, as mentioned above, has no permissions

UFS does NOT work, even though it is the "UNIX File System" - Linux support is read-only.  
Note that just about any filesystem works read only - it's just write support that's limited to the filesystems mentioned above.

Just do what suits you best...

---

### Post by darkmaster on 2007-07-04
> **thully said:**
> Yes, you need to set your uid and gid (user id and group id) to 501.  You can do this with the usermod and groupmod tools - make sure you open a root shell (sudo su) before using.  You'll also need to chown / chgrp your entire home directory after changing your uid and gid (to reclaim ownership).

As for sharing filesystems, one can in fact share a home directory (search the archives for my recent thread on this).  However, you may have issues if you use the Unix tools often in OS X.  In any case, the filesystems you can use are:

* HFS+ (NON-journaled) This is just the standard OS X filesystem, you can turn off journaling in Disk Utility by selecting a partition, holding down Option and choosing the File menu - Disable Journaling will be there.  You can actually just share your OS X volume and use it for data if you use this for its filesystem.
* HFS+ (Case-sensitive, NON-jorunaled) (This is what you want if you're sharing the home directory, as it is case-sensitive like all Linux filesystems
* FAT32 This is simpler to work with - no permissions are involved, and FAT32 works in every OS you try it in.  You don't have to change the uid and gid of your user to access this.  However, it has limits due to being antiquated (no files over 4GB, most significantly), and, as mentioned above, has no permissions

UFS does NOT work, even though it is the "UNIX File System" - Linux support is read-only.  
Note that just about any filesystem works read only - it's just write support that's limited to the filesystems mentioned above.

Just do what suits you best...

Thanks for the precious info.

I'm going to install a NEW Ubuntu Feisty. So I don't want to change any uid, gid, etc, I want to set them now once for all! So, if during installation I set the username as 501 will everything be OK on the permission side?

---

### Post by grim1234 on 2007-07-04
I don't think you can set the gid / uid etc on install (afaik), but it's easy to do after install. 

I've just reinstalled my system and it worked nicely. No bother with bootcamp or partition sizes. I booted from the osx install cd then partitioned the disk using disk utility from the menu on the cd install. I then set three partitions, one osx 5gb, one anything 5gb, the rest an unjournaled hfs partition. I then deleted the middle partition to leave room for linux. After installing refit from osx, i edited /efi/refit/refit.conf to boot legacy (linux / windows) first. Then I just booted from the ubuntu cd and installed. 

Nice and easy, and ubuntu now boots first, and I have a large partition I can use between both operating systems for files (after installing hfsplus in linux, and adding an entry to fstab).

---

### Post by darkmaster on 2007-07-04
OK then, so I install Ubuntu and set which username?
I need step by step assistance boyz, please. I already created the appropriate partitions, that part is OK so forget about it. Let's concentrate on permissions.
Now, list me some steps please :) 
1) I install Ubuntu with username ....?
2) If I can choose any user I like, how do I set a different uid/gid after installation? And why should I do it after installing Ubuntu since during install I get the chance to do it once for all?

---

### Post by thully on 2007-07-04
The user name doesn't matter - it's the uid/gid that matter.  You can't set those during install, so that's why you have to do it afterwards.

---

### Post by cyberdork33 on 2007-07-04
if you want to set your uid/gid the same as it is in OSX go for it. I don't know what else you want us to tell you.

All files have an owner that owner has a uid and a gid. These numbers are what the system uses to determine the ownership. There are also set permisssions. user's read/write/execute, group's read/write/execute, and other's read/write/execute. 

if the user's files that you want to access in the OS partition have the same uid/gid then ubuntu doesn't know the difference.

Now then, you do not HAVE to change the uid/gid in either system to have access to your files, you can simply change the file's permission to 'read' for the 'other' group on everything you want access to and you can read them. 

You have all the info you need, now decide what you want to do. If something doesn't work, then try again, experiment.

---

### Post by darkmaster on 2007-07-05
> **cyberdork33 said:**
> if you want to set your uid/gid the same as it is in OSX go for it. I don't know what else you want us to tell you.

All files have an owner that owner has a uid and a gid. These numbers are what the system uses to determine the ownership. There are also set permisssions. user's read/write/execute, group's read/write/execute, and other's read/write/execute. 

if the user's files that you want to access in the OS partition have the same uid/gid then ubuntu doesn't know the difference.

Now then, you do not HAVE to change the uid/gid in either system to have access to your files, you can simply change the file's permission to 'read' for the 'other' group on everything you want access to and you can read them. 

You have all the info you need, now decide what you want to do. If something doesn't work, then try again, experiment.

Ok, sorry for bohering you all so much. My problem as I can see it now is that I don't know what a uid and gid is. I thought I new it but sincerely looks like I don't. I thought that, if during installtion, I setted a username like darkmaster, then darkmaster is my uid. Looks like it is not. So I'll proceed with installation but then I just need an information. 
How can I know my uid and gid once installation is completed and how do I change them?
Do you get why I didn0t understand now? I was sure that the uid was the username, that is what I choose during installation in ubuntu... sorry :(
In any case I'll create a partition with fat32 (I dn't think I'll use files bigger than 2gig) for both systems to share it and a partition for ubuntu plus a little one fo swap, of course. I bought a Macbook with 200 Gig of hard disk just for this task.

---

### Post by darkmaster on 2007-07-05
I'm starting to understand what uid and gid are. So they're like in OSX (At the end osx is nothing but darwin..). I found this thread even if the guy who asked is having problem and nobody replyed animore... do you think it would do the trick right?

[http://ubuntuforums.org/showthread.php?p=2443542](http://ubuntuforums.org/showthread.php?p=2443542)

Let me know if I can use those commands safely.

---

### Post by grim1234 on 2007-07-05
I would follow this :

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook](http://gentoo-wiki.com/HARDWARE_Apple_MacBook)

try to do the changing of the uid / gid from osx if possible, less potential problems that way.

---

### Post by cyberdork33 on 2007-07-05
Just curious, did you see this thread?
[http://ubuntuforums.org/showthread.php?t=486483](http://ubuntuforums.org/showthread.php?t=486483)

It is about having a shared home directory, but it outlines setting up the user permissions correctly on a partition (which is what you need to do.)

> 
1. Change your User/Group ID to match Mac OS X (sudo groupmod -g 501 yourid;sudo usermod -g 501 yourid;sudo usermod -u 501 yourid)
2. Reclaim ownership of your home directory (sudo chgrp -R yourid /home/yourid/*;sudo chmod -R yourid /home/yourid/*;sudo chgrp -R yourid /home/yourid/.*;sudo chmod -R yourid /home/yourid/.*)Finding what your uid/gid is is pretty easy, just type 'id' in a terminal.

---

