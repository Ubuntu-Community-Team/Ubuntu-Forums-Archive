---
title: "I can't get permission to use  new partition"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by Nudgeworth on 2007-10-09
Hello.

 I removed Vista by reformatting It's partition to ext3.
 
 Now I'm unable to access that partition.
 
 Help!

---

### Post by vanadium on 2007-10-09
It is normal that you do not have permissions. The root user (probably yourself) has to give you rights.

I will give you advice to do that that is a bit different than what most people will tell.

* Open a command prompt. Make sure you know the mount point of your former Windows partition. To know this, issue the command at the terminal

mount

First you see the device name, e.g. /dev/sda1. After "on" the mount point is mentioned. Let us assume that is /media/myhd

Then create as root a directory on that drive, and give that directory to yourself as a user. For convenience, link the directory to your home folder. Then, the drive will appear as a normal directory under your home directory for easy access.

sudo mkdir /media/myhd/workingdirectory
sudo chown $USER:$USER /media/myhd/workingdirectory
sudo ln -s /media/myhd/workingdirectory $HOME/mydrive

The last command will create the symbolic link in your homedirectory (you can type $USER and $HOME as is. This is substituted by your user name and home directory, respcectively). Then, you simply can access the drive (and read/write to it) through "mydrive" in your home directory (obviously, you may change the names to your liking).
sudo

---

### Post by anaconda on 2007-10-09
You mean you cant access it anymore? And you used to be able to access it.

That sounds like you still have that partition as ntfs in your /etc/fstab -file. (that is where the info of partitions are)

if that is the case,
just change the ntfs to ext3 from the line that used to boot your windows partition. (propably the only line that has ntfs in it.

you can edit the fstab file by:
sudo gedit /etc/fstab

and after editing that you need to reboot  the machine to re-mount all partitions.

---

