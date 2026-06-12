---
title: "How do I use my extra ext3 partition?"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by tryerouter on 2007-01-18
Before I installed ubuntu 6.10  I made an extra ext3 partition on another drive. This partition shows up as sdb2  on my desktop so I guess it's mounted at startup. I can see it but I can't read or write to it as a normal user. Looks like it's owned by root. Do I have to change permissions or something to use this partition? Like open up a terminal and type in  sudo cmod 777 /dev/sdb2. Would that be the right way to do it?

---

### Post by taurus on 2007-01-18
What's the mount point for /dev/sdb2?  You cannot change permissions on the partition; you can only do that with the mount point.

```
df -h
```

---

### Post by Cobikegeek on 2007-01-19
I think you'll want to use the command 

sudo chmod 0700 /mountpoint/

(replacing /mountpoint/ with the actual mount point when you figure that out).  That gives only user and root read/write/execute permissions.

---

### Post by tryerouter on 2007-01-19
> **taurus said:**
> What's the mount point for /dev/sdb2?  You cannot change permissions on the partition; you can only do that with the mount point.

```
df -h
```
Looks like right now its mounted at /media/sdb2. Well the device manager shows that as "Volume (ext3)" at /media/sdb2 and "block device" at  /dev/sdb2. Change permissions with the mount point? And tell me again what that  df -h  thing does? Thanks.

---

### Post by taurus on 2007-01-19
What is your login name anyway?  For now, I will assume it's **tryerouter** so please substitute the right one.

```
sudo chown -R **tryerouter**:**tryerouter** /media/sdb2
sudo chmod -R 755 /media/sdb2
```
That should make you the owner of /media/sdb2 so you can write and delete whatever you want in there.

---

### Post by tryerouter on 2007-01-19
> **Cobikegeek said:**
> I think you'll want to use the command 

sudo chmod 0700 /mountpoint/

(replacing /mountpoint/ with the actual mount point when you figure that out).  That gives only user and root read/write/execute permissions.
So like, groups and others can't run arounr in there?

---

### Post by tryerouter on 2007-01-19
> **taurus said:**
> What is your login name anyway?  For now, I will assume it's **tryerouter** so please substitute the right one.

```
sudo chown -R **tryerouter**:**tryerouter** /media/sdb2
sudo chmod -R 755 /media/sdb2
```
That should make you the owner of /media/sdb2 so you can write and delete whatever you want in there.
Thanks Taurus. I'll try'er out.

---

### Post by irish_flu on 2007-01-19
I have nothing to add, I just wanted to say "nice avatar".  :)

---

