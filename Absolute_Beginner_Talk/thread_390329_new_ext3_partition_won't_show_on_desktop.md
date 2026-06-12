---
title: "new ext3 partition won't show on desktop"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by daemmon on 2007-03-21
Ok, so here's the problem: after transforming my Windows Vista partition into a linux one (ext3), I can't seem to get ubuntu to show it on desktop anymore. The partition mounts ok and is accessible through nautilus, but it doesn't show up on desktop or in computer/places. The line in fstab is 

# /dev/sda8
UUID=c5a9b020-6b46-4f39-8bc7-f84e4984efd5 /mnt/theStuff     ext3    defaults 0       0

If somebody could help me do it, I would really appreciate it. Thanks in advance

---

### Post by kpkeerthi on 2007-03-21
Change the mount point to /media/theStuff and reboot.

---

### Post by taurus on 2007-03-21
> **kpkeerthi said:**
> Change the mount point to /media/theStuff and reboot.

And don't forget to create a new mount point before reboot or it won't mount.

```
sudo mkdir /media/theStuff
```

---

### Post by daemmon on 2007-03-21
thanks for the help. didn't know that ubuntu only shows folders from /media on the desktop. isn't it possible to change this? not that it is really necessary, just for the record :p

---

