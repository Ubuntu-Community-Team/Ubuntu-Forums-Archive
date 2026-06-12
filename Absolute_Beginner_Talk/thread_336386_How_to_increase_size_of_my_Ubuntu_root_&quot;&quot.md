---
title: "How to increase size of my Ubuntu root &quot;/&quot; partition?"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by flexible on 2007-01-11
Hi,

I have Ubuntu Drapper/XP dualboot 32bit pentium M acer laptop, with 40 GB hard disk.

When i installed Ubuntu, i allotted only 4 GB to the root "/", now that i would like to have more space, how can i achieve that? I have a 2 GB free partition, that i lately Ext3 formatted using System>Admin>Discs utility and assigned "/" access path, yet that doesnt show up in my home folder.

---

### Post by bodhi.zazen on 2007-01-11
Err .... new Hard drive ?

Try GParted:

	Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

	Download: [Download Gparted](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by jvc26 on 2007-01-11
Do you want to make the partition itself (i.e. / bigger) or just add more space within the filesystem tree?

If its just the extra space within the tree you need to mount that 2 GB free partition within a point like /mnt/extra_space

You can't just add it to / as the mount point '/' is already taken by the 4GB partiton.

You can also resize the / partition, deleting that 2GB partition and making the / partition bigger moving it into the space.
Il

---

### Post by flexible on 2007-01-12
hi Illuvator,

> Do you want to make the partition itself (i.e. / bigger) or just add more space within the filesystem tree?

The thing annoying me is the message says "You are running outof space in home (/) directory. 98% used up"

I would like to know, whether the strategy will work if I add free space 2GB to the filesystem? Or shall I extent the memory of / root as such?

When I tried to change from / to /mnt/extra_space it doesnt change. I was wondering what the heck. 

I am a novice.

Hi bodhi.zazen,

I have QT Parted installed in my ubuntu , but it cant identify any partitions. message comes: "Error, cant identify any partitions,are you root?"

---

### Post by bodhi.zazen on 2007-01-12
;) flexible

Try running from a terminal with gksudo:

```
gksudo qtparted
```

for a password, use your log-in password...

---

### Post by kpkeerthi on 2007-01-12
Run qtparted or gparted using livecd. The partition you are resizing should not be mounted.

---

