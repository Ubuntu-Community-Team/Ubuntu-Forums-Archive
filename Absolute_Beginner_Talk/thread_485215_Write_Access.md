---
title: "Write Access"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by Adamas on 2007-06-26
Is there a reason that I cannot write to my own USB drive? Ubuntu is telling me that I do not have permission to write to it. Thanks

---

### Post by defrex on 2007-06-26
Maybe it's NTFS? Try running this:
```
sudo apt-get install ntfs-3g
```

---

### Post by bodhi.zazen on 2007-06-26
> **Adamas said:**
> Is there a reason that I cannot write to my own USB drive? Ubuntu is telling me that I do not have permission to write to it. Thanks

post the output of 

sudo fdisk -l

---

### Post by JRR883 on 2007-06-26
> **Adamas said:**
> Is there a reason that I cannot write to my own USB drive? Ubuntu is telling me that I do not have permission to write to it. Thanks
Are you trying to transfer the files in the window that pops up when you plug it in? If so, you probably don't have the permissions to write to its mountpoint. Run **sudo nautilus /path/to/usbdrive** and you should have permissions to write to it.

---

