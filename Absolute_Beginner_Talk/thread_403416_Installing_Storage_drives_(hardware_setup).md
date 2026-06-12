---
title: "Installing Storage drives (hardware setup)"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by rshanson1980 on 2007-04-07
I have a storage drive that shows in my device manager.  For some reason it has a block on it.  I cant get into it.  Do I have to install windows to get to it?  

Also is there a way i can play dvds or is it hopeless?

---

### Post by confused57 on 2007-04-07
> **rshanson1980 said:**
> I have a storage drive that shows in my device manager.  For some reason it has a block on it.  I cant get into it.  Do I have to install windows to get to it?  

Also is there a way i can play dvds or is it hopeless?

You need to mount it first:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

if it's an external drive, mount it using the above instructions for mounting the filesystem(FAT32?)...once you make a directory, open your device manager, then change the mountpoint to whatever you named it, then you click on I think it's "Enable" then "Browse".

See this section from the link I gave you:
>  Make a 'Mount Point'.
Either type, or copy and paste the following code into your terminal,
code:
ubuntu@ubuntu:~$ sudo mkdir /media/windows
That makes a 'mount point' (a directory in which to mount the other filesystem in the filesystem you are using now). This directory will be named 'windows', and located in my /media directory.  The /mnt directory is another popular place for the mount point to be created.

5) Mount the other filesystem with an appropriate mount command,
If your other filesystem is formatted as FAT32, you may type or copy and paste the following code into your terminal,
code:
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /media/windows -t vfat -o umask=000
(Where the Windows system has the FAT32 filesystem).]

If it's an internal hard drive, read the section for adding an entry to your /etc/fstab for the different filesystems.

---

