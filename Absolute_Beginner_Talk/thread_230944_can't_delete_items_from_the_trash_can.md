---
title: "can't delete items from the trash can?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by lime4x4 on 2006-08-06
if i right click the trash can and select empty trash nothing happens.
If i open the trash can then manualy delete each file i can
Any ideas?

---

### Post by andb on 2006-08-12
Had the same problem. Mine is called Garbage Bin, replace this with whatever your localized version is. It wouldnt empty with rightclick > Empty Garbage Bin, reported the wrong number of files. 

First, delete the .Trash folder from each user account. Replace USERNAME with each user account on your system.
```
sudo rm -rf /home/USERNAME/.Trash
```

Remove the garbage bin from the panel. Reboot. Add the garbage bin to the panel. After this, mine works fine.

---

### Post by user1397 on 2006-08-12
yep this usually happens when you put something with root permissions into the trash, so that it can only be deleted with root permissions.  you could either do the graphical method (ALT+F2 > gksudo nautilus) or using the terminal.

---

