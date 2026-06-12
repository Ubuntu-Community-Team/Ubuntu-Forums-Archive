---
title: "grub 1.5 error 17"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2007-11-13
I got grub error 17(7.04) , Haven't made any changes to my system, somebody advised that I reinstall grub from live CD.

How do I do that???

---

### Post by bulldog on 2007-11-13
17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. 

Please post the output of```
sudo fdisk -l
```

---

### Post by alienexplorers on 2007-11-13
Use the Super Grub Disk to reinstall Grub.  I have a link to it in my sig line.

---

