---
title: "Can't mount hfsplus drive."
date: 2006-05-17
forum: Apple PPC Users
---

### Post by omjaroo on 2006-05-17
Hi,

I have installed a hard drive that I used as a backup for my g5. It has lots of music and photos on it.

I typed the following in a terminal gnome terminal window:
jared@ubuntu:~$ sudo mount -t hfsplus /dev/hdb /mnt/backup

and I get the following:
mount: /dev/hdb already mounted or /mnt/backup busy

The mount command does not indicate that the volume is mounted and umount says that it is not mounted. 

Any ideas?

Thanks for you consideration.

Jared

---

### Post by pindar on 2006-05-25
Are you sure about the names? On a G5, hard drives typically should be **sd**<a|b|c...>, not hd, that's typically the cdrom.

---

### Post by digs on 2006-06-17
Do you have hfsplus in the kernel? If not run "modprobe hfsplus" as root and retry the mount.

---

### Post by bodhi.zazen on 2008-10-10
I see this is a very old thread , but it comes up high in ye ole google search ...

You need to identify the partition

/dev/hda = the entire hard drive.

You need to use 

/dev/hdb1

or with more recent versions of Ubuntu

/dev/sdb1

Use:

```
sudo fdisk -l
``` to list your partitions

and see also :

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018")

---

