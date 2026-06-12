---
title: "CD and DVD drive emulation?"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by Boris-- on 2007-06-05
Is there a way to do this, like deamon tools in Ubuntu? Thanks in advance!

---

### Post by taurus on 2007-06-05
Do you meant mouting .iso?

```
sudo mkdir /media/iso
sudo mount -t iso9660 **filename.iso** /media/iso -o loop
```

---

### Post by Boris-- on 2007-06-05
Wow, that's cool. Now how about mounting other formats? like alcohol's .mdf and .mdf, and others? Is there a way too?

---

### Post by steeleyuk on 2007-06-05
You might want to take a look at [this]("http://onlyubuntu.blogspot.com/2007/06/mount-and-unmount-isomdfnrg-images.html")

---

