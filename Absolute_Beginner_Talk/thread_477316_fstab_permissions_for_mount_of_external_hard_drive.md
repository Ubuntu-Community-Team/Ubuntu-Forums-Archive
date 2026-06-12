---
title: "fstab permissions for mount of external hard drive"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ~sparkles~ on 2007-06-18
I have started getting the hang of mounting things in kubuntu. Unfortunately it only auto mounts small FAT usb memory sticks, but not External NTFS large hard drives (bug maybe?)

Anyway, I mounted the external hard drive but the permissions haven't behaved nicely. Can someone tell me if I've made the right modifications of fstab?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=9f186a36-e890-4979-89bf-06c40697af70 /               ext3    defaults,erro$
# /dev/sda6
UUID=85933306-9b4c-43c1-a17d-70cf3f149068 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5 /media/fat vfat auto.users.umask=000 0 0
/dev/sdb1 /media/storage ntfs nls=utf8,umask=0222 0 0

```

Thanks :)

---

### Post by Inxsible on 2007-06-18
> **~sparkles~ said:**
> I have started getting the hang of mounting things in kubuntu. Unfortunately it only auto mounts small FAT usb memory sticks, but not External NTFS large hard drives (bug maybe?)

Anyway, I mounted the external hard drive but the permissions haven't behaved nicely. Can someone tell me if I've made the right modifications of fstab?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=9f186a36-e890-4979-89bf-06c40697af70 /               ext3    defaults,erro$
# /dev/sda6
UUID=85933306-9b4c-43c1-a17d-70cf3f149068 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5 /media/fat vfat auto.users.umask=000 0 0
/dev/sdb1 /media/storage ntfs nls=utf8,umask=0222 0 0

```

Thanks :)

You should use pmount for mounting external drives and usb sticks. You can install pmount like so
```
sudo aptitude install pmount
```

Also your line for /dev/sda5 looks incorrect. They should be commas, not periods

---

### Post by ~sparkles~ on 2007-06-18
Ok. Installed pmount but it requires root permission to open external hard drive.

---

### Post by bren on 2007-06-18
> **~sparkles~ said:**
> 

Anyway, I mounted the external hard drive but the permissions haven't behaved nicely

did you know ubuntu won't write to NTFS by default?
maybe you think this is a permissions problem

if so do the following

```
sudo apt-get install ntfs-3g
```

then run ntfs-config

hope this helps

bren

---

### Post by ~sparkles~ on 2007-06-19
Already have done that too. I can't even look at the external hard drive without root permission. Is there a setting I need to use for pmount?

---

### Post by Tech_Power888 on 2007-12-24
i too cannot seem to get access to my external hdd. i have tried everything above but nothing seems to work. i'm a total noob so any help would be appreciated.

p.s i am not even sure how to be root user. if someone can show me how to do this i'm confident i can then see the ext. hdd.

thanks 

ryan

---

### Post by lgambett on 2007-12-24
read carefully the post from bren, if you did not install the ntfs-3g package you will never write on your external HDD.

---

### Post by Paqman on 2007-12-24
> **lgambett said:**
> read carefully the post from bren, if you did not install the ntfs-3g package you will never write on your external HDD.

NTFS write permission through ntfs-3g is now installed by default.

---

### Post by buntu_hugenewbie11 on 2008-01-25
So is there a way to set up permissions to be automatic with external hard drives?
This has been a huge headache for a few of us.
I have an external drive with 2 partitions and I want to back up data on my linux drive with it.
So when I plug in the drive the system sees it as a kde window pops up for both partitions.
for the ntfs section I get a weird error: hal-storage-removable-mount-all-options refused
And the ext3 partiton never has write permissions.

Is there a way a that simplelton newbie such as myself can find a way to configur the system so that everytime I plug in my external drive it gets mounted and permissions to read and write become automatic??
I think a lot of us coming from windows would like to be able to figure out how to do this.

---

