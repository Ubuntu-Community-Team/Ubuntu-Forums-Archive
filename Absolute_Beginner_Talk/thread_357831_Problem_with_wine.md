---
title: "Problem with wine"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by valtru on 2007-02-10
I'm getting this error whenever I run winecfg 

```
wine: creating configuration directory '/home/valtru/.wine'...
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
Failed to open the service control manager.
```

This was a succeeding error after fixing this error:
```
ALSA lib seq_hw.c:457snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
```
This problem was fixed after I did:
```
sudo modprobe snd-seq-oss
```
and removing /etc/asound.conf

How do I go about fixing that? Please help out a poor beginner here :(

---

