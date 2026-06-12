---
title: "secondary drive permissions"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by ofb on 2007-03-15
How do I change ownership of my other drives?

Background: My devices in /media are owned by root. That's fine, but sometimes I'd like to set my user-level permission for a directory or file to ReadOnly briefly, to protect it during operations. But it seems a user cannot set restrictions on his own level when the device is owned by root.

So I went into Nautilus as root to change drive ownership to user, but I get a dialog saying I cannot change ownership.

So... how do I change ownership then? And/or is there another way a user can restrict his own access momentarily that I've missed? (Other than jumping in and out of root of course.)

---

### Post by Smaug067 on 2007-03-15
I use:
gksudo nautilus 
to access my extra hard drives.

---

### Post by kelbizzle on 2007-03-15
thats odd. I'm able to change the files and folder located on my extra drive. It is also owned by root. I can change the files and folders to read only. How do you have the drive mounted. heres and example of the line I used to mount my fstab
```
/dev/hdb1 /media/xxtra reiserfs defaults 0 0
```

---

### Post by aysiu on 2007-03-15
One of these should help you:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ofb on 2007-03-15
Smaug067,

Access is fine, but I cannot change the ownership of the drive with gksudo nautilus. You can?


kelbizzle,

/dev/hdd1 /media/hdd1 vfat rw,user,fmask=0111,dmask=0000 0 0

---

### Post by kelbizzle on 2007-03-15
> **ofb said:**
> Smaug067,

Access is fine, but I cannot change the ownership of the drive with gksudo nautilus. You can?


kelbizzle,

/dev/hdd1 /media/hdd1 vfat rw,user,fmask=0111,dmask=0000 0 0

> /dev/hdd1    /media/hdd1 vfat  iocharset=utf8,umask=000  0    0

back up your fstab and try this then..
```
sudo mount -a
```

---

### Post by aysiu on 2007-03-15
kelbizzle's right on about what you need to do, as you can't *chown* a FAT32 partition.

For more step-by-step instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by ofb on 2007-03-15
Well, I've been reading for a couple of hours and have only succeeded in making my little knowledge more dangerous. Thanks for all this, and I'm just going to have to revisit the problem later when I have more time.

I /do/ appreciate the above may well work, but the hole I'm stuck in now is trying to figure out precisely why we're using different fstab lines.

---

