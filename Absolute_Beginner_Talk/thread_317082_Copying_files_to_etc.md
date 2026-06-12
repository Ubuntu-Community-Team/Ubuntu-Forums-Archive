---
title: "Copying files to /etc"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by k2pow on 2006-12-11
So in order to install my drivers I need to manually copy two system files to the etc/ndiswrapper/netdelus file. Whenever I try this it says You dont have permissions to write this folder. I thought I was signed on as the root administrator but not sure so any help would be greatly appreciated.

---

### Post by bodhi.zazen on 2006-12-11
> **k2pow said:**
> So in order to install my drivers I need to manually copy two system files to the etc/ndiswrapper/netdelus file. Whenever I try this it says You dont have permissions to write this folder. I thought I was signed on as the root administrator but not sure so any help would be greatly appreciated.

use sudo```
sudo cp file_to_copy destination
```

---

### Post by aysiu on 2006-12-11
If you prefer a more drag-and-drop method, press Alt-F2 and type ```
gksudo nautilus
```

---

