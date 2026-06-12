---
title: "PDF's and permision to edit (stuck in read-only)"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by jeepfreak2002 on 2007-06-07
OK - 2 things.  I am running Feisty, and it appears that I do not have permission to write to PDF files, as they are in read-only format, but I am able to edit them when in Windows.

I want to install Acrobat Reader as well, but when I go to edit the /sources.list file to include an additional repository THAT file is also read-only.  I realize that I need to change the permissions setting, but I do not know where to go.  Any help would be appreciated.

Jeepfreak

---

### Post by Inxsible on 2007-06-07
To enable write access to the pdf files, are you sure you have permissions on the folder or drive that they are in?
Is the drive in ntfs file system? If yes, do you have ntfs-3g installed?
Have you enabled write-access to both internal and external drives?
 
to edit the sources.list you need to be root. Open up a terminal and type in
```
 gksudo gedit /etc/apt/sources.list
```

---

