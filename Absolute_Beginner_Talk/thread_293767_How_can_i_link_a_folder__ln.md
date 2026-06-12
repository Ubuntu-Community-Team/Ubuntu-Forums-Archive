---
title: "How can i link a folder ?? ln"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by drews_blunted on 2006-11-05
I would like to place a link in my /media/sata folder to /media/cdrom so my mythtv setup can access divx movies i put on a cd and insert.

---

### Post by po0f on 2006-11-05
drews_blunted,

This should work, but /media/sata will have to be mounted before the removable media (CD/DVD):
```
$ sudo mount /media/sata
$ sudo ln -s /media/cdrom0 /media/sata/divx
```

Before unmounting /media/sata, you will have to unmount /media/cdrom0, as mount will probably complain about device/resource being busy otherwise.

---

### Post by superm1 on 2006-11-05
No it won't matter the order things are mounted or unmounted after the symlink is created.  FWIW, you will need to change the mythvideo settings as well once you make this symlink.  You need to set it to browse the contents so that you don't need to update the metadata every time you insert a CD.

Also, if you're not logging into a gnome session, you will need to start gnome-volume-manager so that disks can get mounted when you insert them automatically

---

