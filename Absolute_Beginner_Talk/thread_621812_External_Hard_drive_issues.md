---
title: "External Hard drive issues"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by nevr2low on 2007-11-24
hi when i mount my external hard drive in my alienware running ubuntu 7.04 it comes up read only. i loged into root to change the permishions and still it says that i dont have them HELP what do i do?

Thanks

---

### Post by gn2 on 2007-11-24
Press Alt+F2 tick the "run in terminal" box and enter: sudo nautilus

You will now have unrestricted read/write access to ALL your files/partitions/drives (including vital system files) so go carefully.

---

### Post by PmDematagoda on 2007-11-24
Is your drive having an NTFS file system? If so, install ntfs-3g:-
```

sudo apt-get install ntfs-3g
```

then install ntfs-config:-

```
sudo apt-get install ntfs-config
```

then enable external NTFS volumes to be read by ntfs-3g by using ntfs-config found in Applications>System Tools>NTFS Configuration Tool, then see if you can now read the external drive.

---

