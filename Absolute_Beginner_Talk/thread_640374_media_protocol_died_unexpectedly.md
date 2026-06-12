---
title: "media protocol died unexpectedly"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by Cap'n Murph on 2007-12-14
whenever I boot up my system the messages "The process for the media protocol has died unexpectedly" and "The process for the file protocol has died unexpectedly". It doesn't read any of my cd drives or my floppy drive. What do I need to do to fix this?

---

### Post by siciliancasanova on 2007-12-14
First thing I would do is check your error log and post it up here.

---

### Post by quandary on 2007-12-14
check fstab

for the command line:

nano /etc/fstab

should have this entry
```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

If you use dvd-recorder:
```

/dev/dvdrecorder    /media/dvdrecorder  subfs      noauto,fs=cdfss,ro,procuid,nosuid,nodev,exec,iocharset=utf8 0 0

```

---

### Post by Cap'n Murph on 2007-12-14
How do I go about checking the logs? When I do the fstab thing I get:

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

---

### Post by quandary on 2007-12-21
```

var/log/messages 

```
is probably what you are looking for. 

An easy way to see your boot messages is to type
```

dmesg | more

```

or type
```

sudo gedit var/log/messages 

```

---

