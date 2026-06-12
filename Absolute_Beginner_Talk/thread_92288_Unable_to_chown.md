---
title: "Unable to chown"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-19
Well, my Linux install isn't going too well...the issue for this post is that I have a large FAT 32 file as my last partition (mounted as /media/hda7), which I want to use as file storage that can be accessed by both Ubuntu and Windows.  However, my user doesn't have permission to write to this file.  I went to the terminal and tried to change ownership, and the following occurred:

stephen@ubuntu:~$ sudo chown stephen /media/hda7
Password: [my password]
chown: changing ownership of `/media/hda7': Operation not permitted

What am I missing?  Thanks.

---

### Post by vruum on 2005-11-19
I don't think FAT supports permissions, what you should probably do, is edit your fstab like [this]("http://ubuntuguide.org/#automountfat") and remount the partition.

---

### Post by frodon on 2005-11-19
Fat32 file system don't support ownership and unix rights so you will never be able to do such things (chown, chmod, ...) on a FAT32 partition.
However it's not your problem because all you want, if i understand well, is to be able to write on your FAT32 partition as a simple user.
So post here your fstab (in /etc) file and i will show you how modify it to do that.
I give you an example of my fstab line about FAT32 : ```
/dev/hdd5	/mnt/videos	vfat	rw,user,exec,umask=000		0	0
```

---

### Post by deNoobius on 2005-11-19
Frodon, thanks.  Yes, I just want to be able to read and write to the file.  Here is the fstab entry:

/dev/hda7       /media/hda7     vfat    defaults        0       0

---

### Post by frodon on 2005-11-19
Replace your fstab line with this one and it will be ok ;) : ```
/dev/hda7 /media/hda7 vfat iocharset=utf8,rw,user,exec,umask=000 0 0
```

---

### Post by deNoobius on 2005-11-19
Thank you, Frodon!  That issue is solved.

---

