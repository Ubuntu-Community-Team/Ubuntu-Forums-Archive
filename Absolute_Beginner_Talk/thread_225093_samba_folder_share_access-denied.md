---
title: "samba folder share access-denied"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by verbatim210 on 2006-07-29
my windows laptop can **read **the shared folder but cannot **write **to it.  does anyone know the answer thank you :p 

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    writeable = yes
    guest ok = no
    create mask = 0644
    directory mask = 0755

---

### Post by Indras on 2006-07-29
Is your /media/samba/ on a FAT32 partition?

If it is, you'll have to open your /etc/fstab as root and change the umask=007 to umask=0 for that drive, then remount it (or restart your computer).

If it's on ext3, check your permissions of that particular folder (right-click -> properties in nautilus, or "ls -l" in terminal).  If "other" doesn't have write permissions, the windows box won't either.

---

### Post by verbatim210 on 2006-07-29
thanks indras.
turns out i had to...
enable access for "others"

chmod folder name did the trick.

sudo chmod 0777 /path/to/the/shared-folder
sudo /etc/init.d/samba restart

---

### Post by Indras on 2006-07-30
No problem, glad I could help.

---

