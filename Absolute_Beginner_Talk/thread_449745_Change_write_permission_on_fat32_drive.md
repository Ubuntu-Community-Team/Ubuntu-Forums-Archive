---
title: "Change write permission on fat32 drive?"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by meisbored on 2007-05-20
I'm preparing to change my partitions around and such but I need to back up my files from Windows (which isn't working, so I'm going to re-install it) onto my external hard drive. The partition of my main hard drive where my Windows files are is ntfs, and my external is fat32. The only problem I see in the copy-paste process is that I can't put files in the fat32 drive, so I need to change that so I have write capabilities... anyone know what I need to stick in terminal to do that?

---

### Post by meisbored on 2007-05-20
Bump.

---

### Post by meisbored on 2007-05-20
Anyone gonna help me???

---

### Post by Churnd on 2007-05-20
> **meisbored said:**
> Bump.

Show the output of this command from the terminal:
```
mount
```

A FAT32 drive should have write access.  You might need to change the permissions on the directory it's mounted on.  For example say it's mounted on /media/external.  You can determine permissions by entering these commands in order from the terminal:
[LIST]
[*]cd /media
[*]ls -l
[/LIST]

That will show you what the directory's permissions are, and whether or not you can write to it.

---

### Post by meisbored on 2007-05-20
Whoa, when I typed in mount it told me that it's ntfs... I think my brother must have reformatted it when I wasn't home...
Well I think I know what to do next, anyway. Thanks.

---

