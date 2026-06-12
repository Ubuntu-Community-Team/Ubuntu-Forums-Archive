---
title: "Unlock folders"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by dodgerwv on 2007-06-13
I just loaded a dual boot Feisty/Windows system.  I want to delete a couple of files in my documents folder after moving them over from Windows, but they're locked.  I've also encountered this when trying to format a USB drive.  Any ideas?

---

### Post by Sparkster185 on 2007-06-13
Do you get a "Permission denied" message when you try and erase them?  Is another application using them?

---

### Post by Inxsible on 2007-06-13
Its a permissions issue. If you want to take ownership of the folder for good, then do this:
```
sudo chown -R <your username>:<your group> <device mount path>
```
 
 
If you want to ONLY delete those files and leave the permission as is
cd to the folder where the file is and
```
sudo rm filename
```

---

### Post by starcraft.man on 2007-06-13
> **Inxsible said:**
> Its a permissions issue. If you want to take ownership of the folder for good, then do this:
```
sudo chown -R <your username>:<your group> <device mount path>
```
 
 
If you want to ONLY delete those files and leave the permission as is
cd to the folder where the file is and
```
sudo rm filename
```

Adding to Inxsible. If these folders/drives are formatted with ntfs, you need the drivers for it. Search the forums for "ntfs-3g driver" and you will find guides how to do it. These drivers allow full write access to these drives, Ubuntu mounts ntfs but as read only.

If it is just permissions, his fix will work. [Read this section of linux command for more info.]("http://www.linuxcommand.org/lts0070.php") Its a good tutorial to understand the underpinnings of the permissions system.

---

### Post by dandixon on 2008-03-08
I have the same problem. What would I put as group. Sorry very new to lunix.

---

### Post by Inxsible on 2008-03-08
> **dandixon said:**
> I have the same problem. What would I put as group. Sorry very new to lunix.

your group is the same as your user name, unless you have specifically changed it. Since you are new to Linux, you probably haven't changed your group yet.

---

### Post by dandixon on 2008-03-09
thanks for all your help.
I'm getting the hang of it slowly

---

### Post by forrestcupp on 2008-03-09
> **starcraft.man said:**
> Adding to Inxsible. If these folders/drives are formatted with ntfs, you need the drivers for it. Search the forums for "ntfs-3g driver" and you will find guides how to do it. These drivers allow full write access to these drives, Ubuntu mounts ntfs but as read only.


Didn't Feisty come with ntfs-3g pre-installed?

---

