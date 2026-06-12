---
title: "viewing HFS + drives"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by Loki57701 on 2007-12-21
i have an external WD hard drive i use for my mac and I want to copy some things from there onto my ubuntu box but it doesnt seem to be able to read HFS+ formatted drives. Is there a fix for this?

---

### Post by ajmorris on 2007-12-21
you can do in a command line:
```
sudo mount -t hfsplus /dev/<drive> /mnt/<folder for drive>
```

And there is also a package for hfs disks:
```
sudo apt-get install hfsplusutils
```

---

