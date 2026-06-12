---
title: "Just intalled ubuntu, external hard drive question"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by Dustout on 2007-12-30
I have just intalled ubuntu on my harddrive, after cruising around for a bit i plugged in my external hard drive (150GB) and ubuntu says that their is only 15GB remaining on it, whereas windows says their is 100+GB remaining. 

Also if it helps it is a Western Digital pocket harddrive that uses the Fat 32 filesystem

---

### Post by taurus on 2007-12-30
What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

