---
title: "How Do I find and open my system32 folder"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by Gigidy5 on 2007-10-05
How Do I find and open my system32 folder


And wheres my "Fake C Drive" ?

---

### Post by bsharp on 2007-10-05
If you mean in WINE, then it is a hidden folder in your Home folder.  to see it open Nautilus and then do Control+h i think and to see it in a Terminal type ls -a.  Look for .wine and inside that look for drive_c

---

### Post by jordanmthomas on 2007-10-05
In linux, partitions don't get drive letters (which you seem to understand)
this command will tell you where everything is mounted
```
mount
```

If you don't see your partition listed (it'll be vfat or fuseblk or ntfs-3g or something similar) then look up how to mount windows drives...it's not too hard.


If the above sounds like it's not answering your question, perhaps you are referring to your fake wine c: drive?  It should be located in
```
~/.wine/drive_c
```

---

### Post by Gigidy5 on 2007-10-05
Still don't get it.... 


How do i get to there

Terminal?

---

### Post by Kilz on 2007-10-05
Where do you want to get, do you want to see the application wine's system32 folder, or are you asking if linux has a system32 folder?

If its wine open up your home folder, click Go then Location. A addres space will open , type in (or copy and paste)```
~/.wine/drive_c
``` and hit enter

---

### Post by por100pre1 on 2007-10-05
It should be in: ~/.wine/drive_c/windows/system32 inside your user folder. Press Ctrl+H in Nautilus to see hidden files.

---

### Post by Gigidy5 on 2007-10-05
Thank You

---

