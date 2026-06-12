---
title: "Unable to mount external hard drive."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Neon_Knight on 2007-09-11
I have seen several posts on this topic, but none of the "fixes" have actually worked.

Ubuntu 7.04 LTS auto mounts the External hard disk drive, I can browse the files but I am unable to write to the drive, as it is "read only".

the following is what I have tried:

```

steven@steven-laptop:~/Desktop$chmod: changing permissions of `/media/disk': Read-only file system 
#yes I tried "sudo"

steven@steven-laptop:~/Desktop$ sudo umount /media/disk
steven@steven-laptop:~/Desktop$ sudo mkdir /media/external
steven@steven-laptop:~/Desktop$ sudo mount -t vfat -o rw /dev/sdb1 /media/external
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

steven@steven-laptop:~/Desktop$ 

```

Any help would be greatly appreciated.

---

### Post by jnorthr on 2007-09-11
This may not be a permissions issue rather the partition type you are trying to write to is not what you think it is. Do you know for sure the partition on the external drive is vfat ?

Did you see this thread ? [http://ubuntuforums.org/showthread.php?t=517445](http://ubuntuforums.org/showthread.php?t=517445)

---

### Post by bodhi.zazen on 2007-09-11
Well, I think the problem is with -o rw

Try : ```
sudo mount -t vfat [color=blue]**-o umask=000[/color]** /dev/sdb1 /media/external
```

 * Those are 3 zeros

---

### Post by Neon_Knight on 2007-09-11
I have determined that it is NTFS.

...what must I change in the above terminal commands to make this thing work?

---

### Post by Neon_Knight on 2007-09-11
I have tried the above things.

It complains that it is read only when I attempt to add files to it, and I don't know how to solve this issue.

---

### Post by bodhi.zazen on 2007-09-11
LOL

If it is ntfs, check out ntfs-config :

[http://ubuntuforums.org/showthread.php?t=337970](http://ubuntuforums.org/showthread.php?t=337970)

---

### Post by Neon_Knight on 2007-09-11
I have Ubuntu 7.04LTS.

From what I'm aware, that already has ntfs support with ntfs-3g...

It's already installed.  But it doesn't like the external hard drive.

---

### Post by qpieus on 2007-09-11
Who owns the /media/external directory? I'm guessing it's root. Find out by:```
ls -la /media/external
```

If needed, change that directory's owner to you:```
sudo chown username:username /media/external
```

I had a similar problem to your's and that was my problem. The directory was owned by root and I had inadequate permission to write to it.

---

### Post by Beggar on 2007-09-11
You have do a few things.

First make sure ntfs-3g is installed.

Then install ntfs-config, this will give you a dialog in which you need to enable write to external hdd.

Then you need to add the following entry to your fstab for each drive


```

/dev/sdb<wherever> <mountpoint> ntfs-3g defaults,uid="<username>",gid="groupname",force 0 0

```

The force option isnt mandatory, I personally needed it, I recomend you try it both ways, if you dont need it, ignore it.

Thats the only way I have been able to get my external ntfs hdd to mount with rw.

---

