---
title: "Permanently UNmounting partitions"
date: 2006-08-01
forum: Absolute Beginner Talk
---

### Post by calvinthomas on 2006-08-01
Ok, hopefully this will be my final beginner question because it should be that everything is set up! After changing to Ubuntu 32bit, I have my windows partitions loading on bootup, if I disable them by right clicking and selecting unmount they come back at bootup, similarly if I go system > administration > disks.

How can I disable these so they don't restart at bootup?

Calv

---

### Post by aysiu on 2006-08-01
Press Alt-F2 ```
gksudo nautilus
``` This will launch the browser with root privileges. Go to the /etc directory and back up and then edit the file called *fstab*. Look for the line that has your Windows partition on it (it'll have NTFS or FAT32 in it somewhere) and put a # sign at the beginning of the line. Then save and exit. That's it.

An example...
**Before**: ```
/dev/hda1 /windows ntfs defaults 0 0
``` **After**: ```
#/dev/hda1 /windows ntfs defaults 0 0
```

---

### Post by calvinthomas on 2006-08-01
That worked great, thankyou!

Calv

---

### Post by Bragador on 2006-08-08
I actually had the same question and posted it before finding this. Thanks !

---

