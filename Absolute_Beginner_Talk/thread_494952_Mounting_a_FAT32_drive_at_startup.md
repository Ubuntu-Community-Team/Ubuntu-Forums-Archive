---
title: "Mounting a FAT32 drive at startup"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-07
I know how to mount my FAT32 external hdd manually with sudo mount /dev/sdb1 /media/windows/ -t vfat -o iocharset=utf8,charmask000 but is there some way this can be done automatically each time I start-up instead of having to do it manually each time?

---

### Post by Inxsible on 2007-07-07
there are 2 ways you can do this: But since you have it already mounted, it may just be easier to take step 2...although using pmount is ideal for external drives.

1) you can use pmount to mount it since its an external drive.

2) you can put an entry in the fstab to make sure it automounts. Put this entry in the fstab
```
 /dev/sdb1 /media/windows vfat defaults,auto 0 0
```

---

### Post by tchoklat on 2007-07-07
Mount it in your fstab

---

### Post by snwbord2456 on 2007-07-08
I mounted it in my fstab but when i go to click on the folder it says i dont have permission to view the files.

---

### Post by bodhi.zazen on 2007-07-17
Sorry this is such an old  thread ...

You set your permissions at the time f mount

Add the option uid=xxx, gid=zzz, and umask=zzz

For example :

uid=1000,gid=100,umask=007 will set ownership to your first user, group to users, and permissions of 770

See man mount under FAT for details ...

---

### Post by ugm6hr on 2007-07-17
This explains how to do it too:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

