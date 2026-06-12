---
title: "Recognizing a SATA hdd"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by 713aggie on 2007-04-10
So I recently bought promise sata 300 TX4 and a seagate 500 gig sata hard drive.

It recognized the promise card but not the sata drive. I went to device manager and couldn't find it.

any reason why it might not show up?

---

### Post by mac.ryan on 2007-04-10
Check if you can see it from gparted:

```
sudo gparted
```(you might not have gparted installed, but it is on the repos)

If you can see it from gparted, then it is recognised properly, you just have to mount it (and can use the occasion to partitionate/format it from gparted beforehand.

In order to know how to mount the HD into your system, [this how-to]("http://www.psychocats.net/ubuntu/mountlinux") should get you there.

EDIT: from gparted, you have a list of available HDs on the top right...

---

