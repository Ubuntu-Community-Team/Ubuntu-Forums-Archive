---
title: "Mount question"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by extension on 2007-05-23
I am trying to access a vfat external usb hard drive. When I use GNOME this is very easy because it auto mounts but I am trying to use OpenBox because it runs much quicker on this older machine. 

I found that I can easily mount the drive using 'mount' but I am worried I have done something wrong and am worried I might harm the drive. When I mount under OpenBox I simply use:

mount /dev/sda1 /media/EXTERNAL

After I have done this when I type 'mount' I see:

/dev/sda1 on /media/EXTERNAL type vfat (rw)

but when it is auto mounted under GNOME i see:

/dev/sda1 on /media/EXTERNAL type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

My big concern Is this a problem, is it? 

My second question is I added the above command to /etc/rc.local so the drive mounts on boot but where do I put a command to unmount it? Does it matter? Right now I just make sure to do it before I shut down but obviously I will eventually forget, will that have a grave  outcome?

Thanks

---

### Post by ruy_lopez on 2007-05-23
if you add all the stuff from the Gnome line to fstab, you don't need the stuff in rc.local. Either way, you don't have to explicitly unmount. The halt process will take care of that.

To add to fstab, you would do it like this:

/dev/sda1    /media/EXTERNAL    vfat     rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf    0    0

just make sure its all on one line.

---

