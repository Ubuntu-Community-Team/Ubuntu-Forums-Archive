---
title: "Gmount"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by Zackie on 2008-02-22
Okay So i have Gmount and trying to run an iso... it is a correct iso and i mount it to cdrom and there is a cdrom0 but its says it is not a correct iso.... any :guitar:ideas?

---

### Post by kpkeerthi on 2008-02-22
May be its a corrupted ISO. Did you try with a different one? 
Did the command line work?
```

sudo mkdir -p /media/ISO
sudo mount -o loop /path/to/file.iso /media/ISO

```

---

