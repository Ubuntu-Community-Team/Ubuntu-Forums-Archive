---
title: "NTFS in Kubuntu"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by Cheese Roller on 2007-11-09
How can I read/write to NTFS filesystems in Kubuntu?

---

### Post by lgastmans on 2007-11-09
to me it looks like all you need to do is mount the NTFS partition. Ubuntu has no problem working with NTFS partitions as far as I know.

When I installed Gutsy 7.10, it put an icon on my desktop automatically.

check your fstab file. It should look something like this for NTFS partitions:

# /dev/sda1
UUID=EE08EA1808E9E017 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=137E5AE613AECFF9 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=2E34A48A34A4571D /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=B6D8CCF9D8CCB93F /media/sdb5     ntfs    defaults,umask=007,gid=46 0       1

HTH

---

### Post by Cheese Roller on 2007-11-09
I am aware of that. But my external will not mount in Kubuntu, no problem with Ubuntu.

I tried it in a Vista and it worked fine, so it has to be Kubuntu. A friend had the same problem.

---

### Post by FuturePilot on 2007-11-09
Sounds like this bug
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/115768")
This has seemed to work for some people
```
sudo cp /etc/hal/fdi/policy/20-ntfs-config-write-policy.fdi /usr/share/hal/fdi/policy/10osvendor/
sudo /etc/init.d/hal stop
sudo /etc/init.d/hal start
```

---

