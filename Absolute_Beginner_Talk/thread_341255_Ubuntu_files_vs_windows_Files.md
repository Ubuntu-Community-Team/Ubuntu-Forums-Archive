---
title: "Ubuntu files vs windows Files"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by john38242 on 2007-01-18
Can someone tell me where the files are in ubuntu compare to windows.  C douments ect

---

### Post by jd65pl on 2007-01-18
Your home folder is where you keep your documents.

see this for more info on the linux file structure [http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

---

### Post by gh0st on 2007-01-18
In Windows you tend to get everything under the My Documents folder. So that would be C:\Documents & Settings\$username$\My Documents\

In Linux all of your personal files are stored in the Home folder, which basically does the same job. The path to it would be /home/$username$

Hope that helps a bit. Let me know if you need any more info :D

---

### Post by jvc26 on 2007-01-18
Documents has already been explained, the C:\ is a windows invention for the monitoring of drives. In Linux extra drives may be mounted in /media/$device name$ or /mnt/$device name$ depending on whether it is a removable device or not. The whole filesystem resembles a tree, and extra partitions or drives are merely appended to the tree rather than appearing as separate entities. (The drives are mounted as folders, rather than as separate drives).
Il

---

