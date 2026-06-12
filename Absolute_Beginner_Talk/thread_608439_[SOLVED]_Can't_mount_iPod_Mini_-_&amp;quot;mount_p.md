---
title: "[SOLVED] Can't mount iPod Mini - &amp;quot;mount_point cannot contain...&amp;quot;"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by psyopper on 2007-11-10
Details - 

New to me iPod mini on Feisty.

Originally it was automounting properly but Banshee and GTKPod couldn't access the files. I though I would be smart and I right-clicked the desktop icon, went to properties, file system and changed the mount point.

Now when I plug the iPod in I get:

"Cannot mount the volume"
"Unable to mount the volume 'iPod mini'."
Details: mount_point cannot contain the following characters: ewline, G_DIR_SEPARATOR (usually/)

Now it won't auto mount and when I try to mount I get this:

```

brad@Ubuntu:~$ sudo mount -t vfat /dev/sda /media/ipod
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

So - how does Ubuntu track my mini and mount point? How do I change the default mount point? 

Most importantly - is this even worth it? When it was mounting properly Banshee complained that the music database was too new...

Thanks!!

---

### Post by Nano Geek on 2007-11-10
> **psyopper said:**
> Details - 

New to me iPod mini on Feisty.

Originally it was automounting properly but Banshee and GTKPod couldn't access the files. I though I would be smart and I right-clicked the desktop icon, went to properties, file system and changed the mount point.

Now when I plug the iPod in I get:

"Cannot mount the volume"
"Unable to mount the volume 'iPod mini'."
Details: mount_point cannot contain the following characters: ewline, G_DIR_SEPARATOR (usually/)

Now it won't auto mount and when I try to mount I get this:

```

brad@Ubuntu:~$ sudo mount -t vfat /dev/sda /media/ipod
mount: wrong fs type, bad option, bad superblock on /dev/sda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```So - how does Ubuntu track my mini and mount point? How do I change the default mount point? 

Most importantly - is this even worth it? When it was mounting properly Banshee complained that the music database was too new...

Thanks!!I think it's saying that you can't have a space in the mount name. Why don't you try **ipod-mini** and see if that gives you an error.

---

### Post by mcduck on 2007-11-10
You are trying to mount the whole disk, instead of mounting a partition.


The right command would be this one:
```

sudo mount -t vfat /dev/sda2 /media/ipod
```

(sda2 becasue the music on ipod are on the second partition, while the first one contains the firmware)

---

### Post by psyopper on 2007-11-11
The answer, of course, was already on the forum. I just forget how terrible the forum's search feature is. Goolge is my friend.

The last entry on the first page solved it:

[http://ubuntuforums.org/showthread.php?t=376404]("http://ubuntuforums.org/showthread.php?t=376404")

---

### Post by toxent on 2008-03-25
Thank you, this code worked and i see my ipod once again.  was a frustrating 2 months.  


The right command would be this one:
```

sudo mount -t vfat /dev/sda2 /media/ipod
```

(gusty)
alice

---

