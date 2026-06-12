---
title: "Accessing other hard drives and partitions?"
date: 2005-11-29
forum: Absolute Beginner Talk
---

### Post by orion2087 on 2005-11-29
Howdy, I've just installed ubuntu for the first time, this also being my first linux experience!

I've just installed it, and now I'd like to access my storage hard drive (NTFS) so I can get my wireless drivers and try to figure out ndiswrapper.. but any drive that I try to access, it tells me i'm not aloud! What do I do?

---

### Post by aysiu on 2005-11-29
You need only three things:

This website:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

This command: ```
sudo fdisk -l
```

This knowledge:
NTFS is read-only

---

### Post by orion2087 on 2005-11-29
Alright, I'll give it a shot. And what does the fdisk command do to all of that?

---

### Post by akiro.yamamoto on 2005-11-29
sudo fdisk -l will LIST all drives and partitions

---

