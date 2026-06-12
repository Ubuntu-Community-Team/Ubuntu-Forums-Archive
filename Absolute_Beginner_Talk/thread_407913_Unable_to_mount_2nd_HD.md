---
title: "Unable to mount 2nd HD"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by christo16 on 2007-04-12
Hello, I am using Edgy and I cannot mount my second drive.  It will see it but when I try to "Enable" it, it won't work.  The other drive also has Dapper on it but I believe it has AMD64 bit version installed, if that matters.
Any help is appreciated, thank you!
-Chris

---

### Post by taurus on 2007-04-12
Well, you can mount it from a terminal like

```
sudo mkdir /media/dapper
sudo mount -t ext3 /dev/hda1 /media/dapper
```
Assuming /dev/hda1 is what you want to mount.

Or look at this guide then.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

