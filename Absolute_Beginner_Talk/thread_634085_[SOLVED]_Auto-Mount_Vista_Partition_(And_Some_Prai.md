---
title: "[SOLVED] Auto-Mount Vista Partition (And Some Praise :p)"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Joeb454 on 2007-12-07
Ok first I'll start with the praise :)

I just tried out rythmbox, and I'm pleased because it plays all my itunes music straight from a mounted Vista partition, and I've even set the iTunes folder on there as the default music location, and to check for new files, so I've got all my music when I boot into 'buntu :) Mark me impressed :lolflag:

Problem is...now I'll have to mount that every time I want to listen to music...not a big deal, but its a bit of hassle, because I have to go and specifically mount it, then put in my password, and I'd rather not.

Is there any way I can get 'buntu to auto-mount the Vista partition when I boot up without me having to put in my password?

---

### Post by lamalex on 2007-12-07
Why is it asking for a password, is it your sudo password it's asking for? Or is the volume encrypted and needs a key to be read? I don't know enough about Vista's drive encryption to know if that case is even possible.

Assuming it's asking for your Ubuntu user password, the way to have the drive automounted is to add it to /etc/fstab.

fire up your favourite editor, and add a line into that fine. it will look something like
```

# This is my vista Drive /dev/hdaX
UUID=<execute ls -lah /dev/disk/by-uuid to get this ID> /media/vista ntfs 0 1

```
something like that. Be sure to also create the mount point directory where you're going to be mounting the drive. You've probably already done this if you've been mounting it via the command line. Hope that helps!

---

### Post by Joeb454 on 2007-12-07
Its the sudo password it's asking for. And I'm not mounting via command line, so I'll probably need step by step guides...I've been using Ubuntu for a while, but never done anything like this lol

---

### Post by taurus on 2007-12-07
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
gksudo ntfs-config
```
And point it to your ntfs partition.  It will add an entry in /etc/fstab for your so it will be mounted each time you boot Ubuntu.

---

### Post by Joeb454 on 2007-12-07
Excellent thanks it worked :) Now I have Ubuntu working like a charm on my lappy :)

---

### Post by ace007 on 2007-12-17
Thanks, that was the most concise answer I have found yet.  Great Work.

---

