---
title: "remounting ntfs ppartitions"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by shanike on 2007-06-20
today i booted to my ubuntu instalation and found out that my ntfs partitions got unmounted for some reason. how do i remount them?

---

### Post by finer recliner on 2007-06-20
```
sudo mount /dev/hda1 /media/drive 
```

where "hda1" is the device name of your drive and "drive" is the directory you typically mount to.

to set your computer up so that it auto mounts your drives at boot edit your fstab:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by shanike on 2007-06-21
actually, as i have found out, it's not a problem of mounting:

[IMG]http://img146.imageshack.us/img146/5754/mountyq2.png[/IMG]

what now? :(

---

### Post by shanike on 2007-06-23
ok, i've managed to mount my ntfs partitions to certain mountpoint, how do i grant read/write rights to users (myself)?

---

### Post by Inxsible on 2007-06-23
```
sudo chown -R <your username>:<your group> <device mount point>
```

---

### Post by finer recliner on 2007-06-24
you need ntfs-3g installed to be able to write to an NTFS partition. without it, you can only read from it.

---

