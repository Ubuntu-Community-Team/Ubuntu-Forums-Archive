---
title: "Renaming the Default Mount Points like sda1 or sdb5"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2006-12-04
Hello!

I was wondering how I could rename my NTFS-3G drives from sda1 and sdb5 to something a little more meaningful.  

Here is a copy of my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda8       /home           ext3    defaults        0       2
/dev/sda1       /media/sda1     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5       /media/sdb5     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I have already tried to change the name directly like this:
```

/dev/sda1       /media/Windows     ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sda5       /media/MyDocuments ntfs-3g defaults,locale=en_US.utf8 0 0

```
After a restart, the media never mounted.

I just want these two drives to show up on my desktop as "Windows" and "MyDocuments" rather than "sda1" and "sdb5".  I'm sure this is possible, but I'm in some need of help please! 

Thanks in advance!

---

### Post by bodhi.zazen on 2006-12-04
fstab looks fine.

make your mount points:```
sudo mkdir /media/Windows /media/MyDocuments && sudo mount -a
```

post any error messages...

---

### Post by SendDerek on 2006-12-04
I didn't get back in time!  It sounds like I did the right thing though based upon your recommendation zazen.

I tried the same thing as before again but this time I created two folders in my /media directory to match up with what I was trying to create.  

That might have been the hard way around it, but it worked!

Thank you very much for the interest!

---

