---
title: "Delete a folder"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by chager on 2007-08-28
Delete a folder

I want to delete the Windows folder in File System.  It was installed during the installation.

The path is:  Home >> File System >> Windows

Root is the owner of the folder.  How do I get to root to delete this folder?

Thanks

---

### Post by s26c.sayan on 2007-08-28
In a terminal :
sudo rm -r /path/to/folder

---

### Post by Fonon on 2007-08-28
Windows folder, huh?  Are you dual booting, or running WINE?  I think they are created when you do that, but I'm not certain.  As for root, my friend sucess logging into root with the following information:
user: root
pass: root

alternativly, you can do this in the terminal:
```
sudo rm "path to file"
```

replace "path to file" with the path to your folder.

---

### Post by chager on 2007-08-29
It's the windows partition.

Thanks

---

