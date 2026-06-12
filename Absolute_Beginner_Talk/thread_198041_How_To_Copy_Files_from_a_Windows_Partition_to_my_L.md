---
title: "How To Copy Files from a Windows Partition to my Linux Partition?"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Rinulin on 2006-06-16
I'm a complete Linux newb. So, I figured this is the right place for a question from me ;) 

I've managed to successfully install Ubuntu 6.06 on my PC. I have both a Windows partition and my Ubuntu partition.

The first exercise that I am going to undertake is getting World of Warcraft up and running on my Linux distro. I've seen some of the guides posted here on the forum, but one thing that they gloss over is copying the files off of my Windows partition to Linux.

This seems like it would be painfully simple, but I'm not completely sure how it would be done. Could anyone explain it to me?

Thanks.

---

### Post by Glass_Onion on 2006-06-16
I've never had any trouble with just dragging and dropping the files into the folder I want them to go in. ;)

---

### Post by wahman143 on 2006-06-16
Hi,
It is painfully simple for the most part :wink: - all you should have to do is mount your windows partition and copy away.  I'm more familiar with the command line, so this is how I would do it.

Assumption - windows partition is #1 on a regular PATA hard drive:

```

$ sudo mount -t vfat /dev/hda1 /mnt/your_mount_point

```
OR
```

$ sudo mount -t ntfs /dev/hda1 /mnt/your_mount_point

```

Then you just navigate over to /mnt/your_mount_point and copy away!  Note - if it is an NTFS partition, you will be unable to write to the drive.

HTH,
Wah

---

### Post by Rinulin on 2006-06-16
You guys are great! Thanks!

---

### Post by aysiu on 2006-06-16
If you want your Windows partition permanently mounted, go here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

By the way, wahman143's instructions will work only if you browse as root. You'd need to do this instead: ```
sudo mount -t vfat /dev/hda1 /mnt/your_mount_point -o umask=000,iocharset=utf8
``` or ```
sudo mount -t ntfs /dev/hda1 /mnt/your_other_point -o umask=0222,nls=utf8
```

---

### Post by wahman143 on 2006-06-16
@aisyu,
Thx for reminding me of the -o flag - I always seem to forget that one :lol:

@Rinulin,
NP - good luck with it!

Cheers,
Wah

---

### Post by aysiu on 2006-06-16
[QUOTE=wahman143]@aisyu,
Thx for reminding me of the -o flag - I always seem to forget that one :lol:

@Rinulin,
NP - good luck with it!

Cheers,
Wah[/QUOTE]
It's not a big deal. If you browse as root. you can still access the partition: ```
gksudo nautilus
``` or ```
kdesu konqueror
```

---

### Post by Rinulin on 2006-06-16
[QUOTE=aysiu]If you want your Windows partition permanently mounted, go here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]
Thanks Aysiu. So when you refer to mounting your Windows partion, what you mean is allowing Linux to access and navigate throught the file system on that partition, correct? The files are read-only, but I can see everything that I have on Windows?

---

### Post by aysiu on 2006-06-16
Yes, that's correct.

For NTFS they'll be read-only.
For FAT32 they'll be read/write.

---

