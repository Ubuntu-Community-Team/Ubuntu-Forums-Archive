---
title: "FAT32 USB HDD reporting considerably less free space than there is"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by ilovebsod on 2007-06-28
I have a 60GB USB HDD formatted to FAT32.  I recently deleted a lot of data off it, freeing up 50GB.  In Windows this is reported accurately.  In Ubuntu it sees only 6GB free.

what could have caused this and how can I make Ubuntu see the real amount of free space?

Thanks in advance.

---

### Post by southernman on 2007-06-28
look for a hidden trash folder

---

### Post by ilovebsod on 2007-06-28
> **southernman said:**
> look for a hidden trash folder

already did, there was none (I did shift del when I deleted the old files)

---

### Post by kspn on 2007-06-28
If you do a 'du * -sh' on the base folder of the HDD then that should tell you where the space is being used on the drive.
Also a 'df -h' will tell you how big Linux thinks the drive is.

---

### Post by ilovebsod on 2007-06-28
thanks.  I ended up just formatting via a boot floppy and now it's working again.  I'll keep this thread marked for future reference.

---

