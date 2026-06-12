---
title: "i can't see my ntfs partitions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by sayuki288 on 2007-11-01
all my files are in my ntfs filesystems and i need them so i can use wine but icannot see my partitions it just shows up in home>filesystem>media  as a folder

---

### Post by damotor on 2007-11-01
If your system detected them they should be in /mnt/ . You can also take a look to /etc/fstab , that's the file where detected file systems should be. In the other hand, if the filesystem wasn't detected you may have to mount it manually or add it to /etc/fstab and next time you log in it will appear in /mnt/

---

### Post by meborc on 2007-11-01
install a package "ntfs-config" ... it can be accessed from the system menu... this will configure your ntfs partitions and put them in fstab file...

---

### Post by hoges on 2007-11-01
Or, you could upgrade to Gutsy. NTFS support by default. :)

---

