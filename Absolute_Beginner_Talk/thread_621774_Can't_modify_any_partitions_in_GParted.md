---
title: "Can't modify any partitions in GParted"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by sirgogo on 2007-11-24
Hello all:

I used the command : 
```
sudo gparted /dev/sda
```
to load up GParted. It worked fine.

However, now I am unable to modify my partitions. as most things are greyed out. Do I have to unmount the partitions before I can edit them? I don't want to mess anything up.

Thanks a bunch.

---

### Post by schauerlich on 2007-11-24
Try booting from the gparted LiveCD. It should work from there.

---

### Post by forestpixie on 2007-11-24
gparted won't be able to do anything if partitions are mounted - I always use a gparted livecd - download and burn as an iso - then boot with it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Edit - like the man said :)

---

### Post by sirgogo on 2007-11-24
Alright. Thanks guys. I'll give it a shot.

Just wanted to say that it worked.

---

