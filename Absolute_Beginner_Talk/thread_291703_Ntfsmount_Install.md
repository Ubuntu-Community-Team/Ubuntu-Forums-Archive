---
title: "Ntfsmount Install"
date: 2006-11-02
forum: Absolute Beginner Talk
---

### Post by Hahnarama on 2006-11-02
I want to install ntfsmount so I can view my XP drive, if I would ever need to. 

Is there an Idiot's Guide for newbees on installing and mounting?  I have the _Official Ubuntu Book_ on order but until I get it I am stuck.

Thanks in Advance.

---

### Post by Sef on 2006-11-02
Go to [Linux-NTFS]("http://www.linux-ntfs.org/") to read up on installing.  Beware! It is beta, so expect to encounter bugs.

---

### Post by Hahnarama on 2006-11-02
Is there a "better app" for accomplishing the same task?

---

### Post by rccharles on 2006-11-03
> **Hahnarama said:**
> I want to install ntfsmount so I can view my XP drive, if I would ever need to. 

Is there an Idiot's Guide for newbees on installing and mounting?  

The ability to read an NTFS partition is built into Ubuntu.

The NTFS partition may already be mounted, but restrictive permissions may limit your access. To see if it is mounted, do:
sudo mount

Here is  a quick rundown on mounting a NTFS partition.

Start a terminal session, by:
Applications > Accessories > Terminal


To find the name of the partition, do:
sudo fdisk -l 
# note, the l is the lower case letter l.
# this assumes you have one disk and you booted from this disk

You need to make a directory used in mounting the partition
sudo mkdir /media/windows

You need to edit /etc/fstab
and add or change the line
/dev/hda5 /media/windows ntfs nls=utf8,umask=0222 0 0

Change /dev/hda5 as needed.  If you already have a mount, insert or change nls and umask.

Here is one way of editing,
sudo nano /etc/fstab

now, either reboot or issue the command

sudo mount -a

---------

This web site will show you how to make the NTFS partition read/read.  It will also give you more info on the commands I used above. I do not know if this is the best way to make the NTFS partition read/write.

[http://www.arsgeek.com/?p=675](http://www.arsgeek.com/?p=675)


Robert:)

---

### Post by Hahnarama on 2006-11-03
Robert,

When I try /etc/fstab

I get the following error

no write permission for /etc/fstab

Any clue what I am doing wrong? The rest of your advice was dead on perfect. I fouind my NTFS disk(/dev/hda1) 

Thanks

---

### Post by givré on 2006-11-03
> **Sef said:**
> Go to [Linux-NTFS]("http://www.linux-ntfs.org/") to read up on installing.  Beware! It is beta, so expect to encounter bugs.
There is actually two version of the fuse driver :
- ntfsmount, which is an almost read/write driver, which lake of many feature in write support. [http://www.linux-ntfs.org](http://www.linux-ntfs.org)
- ntfs-3g, improve version of ntfsmount, full read/write support : [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/), actually in beta, but read/write support is stable.

---

### Post by rccharles on 2006-11-03
> **Hahnarama said:**
> Robert,

When I try /etc/fstab

I get the following error

no write permission for /etc/fstab

Any clue what I am doing wrong? The rest of your advice was dead on perfect. I fouind my NTFS disk(/dev/hda1) 

Thanks

You need to put sudo in front of the edit command.

sudo nano /etc/fstab

When I have a number of root commands to do, I do this:

sudo bash

# bunch of commands
# be careful

# when done,  issue the exit command
exit


Thanks for you feedback.

Robert

---

