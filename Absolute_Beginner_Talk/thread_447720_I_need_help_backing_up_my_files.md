---
title: "I need help backing up my files"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Gergless on 2007-05-18
I broke my windows install 

Now im running the live ubuntu ultimate cd , I need to know how i can access the files from my windows install so i can put them onto cd or dvd so i can do a format and fresh install of ubuntu.

thanks

---

### Post by taurus on 2007-05-18
You need to mount your Windows partition before you can access it.  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by Gergless on 2007-05-18
this is what I got.


Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30400   244187968+   7  HPFS/NTFS
/dev/hda2           30401       30401        8032+   f  W95 Ext'd (LBA)

---

### Post by taurus on 2007-05-18
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
df -h
```
Now, you can use nautilus to browse your Windows partition under /media/windows.

---

### Post by Gergless on 2007-05-18
thanks , Everything seemed to work fine .

when i try to access media/windows through the file browser I get an error , I assume I must use nautilus?
but what is nautilus ?

---

### Post by Vixis on 2007-05-18
Nautilus is the default graphical file browser in Ubuntu.

What kind of error you get?

---

### Post by taurus on 2007-05-18
What kind of error did you get?  Nautilus is Gnome file manager, Places -> Home Folder.

---

