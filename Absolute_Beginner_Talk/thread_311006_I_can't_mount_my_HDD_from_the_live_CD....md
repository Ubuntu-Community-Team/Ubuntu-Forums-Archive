---
title: "I can't mount my HDD from the live CD..."
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by blasedeviant on 2006-12-02
I get an error saying /dev/sda1 wasn't found in fstab or mtab... how do I solve this?

---

### Post by Bachstelze on 2006-12-02
If you mount a drive *via* the mount command and it is not in your fstab, you need to specify a mount point for it. What are you trying to do ?

---

### Post by blasedeviant on 2006-12-02
I specified the mount point as /mnt/HDD and still get the error. I'm trying to mount my half-installed Ubuntu partition to install GRUB manually.

---

### Post by bodhi.zazen on 2006-12-02
Mount with sudo...

```
sudo mkdir /mnt/HDD
sudo mount /dev/sda1 /mnt/HDD
```

---

