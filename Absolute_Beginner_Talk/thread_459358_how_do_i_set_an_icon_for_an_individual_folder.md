---
title: "how do i set an icon for an individual folder?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by mijj on 2007-05-30
how do i set an icon for an individual folder?

+ ... how can i set the folder to be deletable by root only (i.e. get the password request dialoge if i try to delete) .. not the contents .. just the folder.  I dont want to accidentally delete this folder.  The contents i wanna treat as normal user stuff.

---

### Post by kernel tom on 2007-05-30
if you right click on the folder and go to Properties.. you should  be able to click on the icon that it is now to bring up icon selections, then choose from there

to get the folder and it's contents to be only executable by root do the following

sudo chmod -R 744 foldername

744 breaks down as follows
7- root can r-w-x
4- group can r-
4- global can r

you will have to remove the files/ folder from the command line tho using sudo


EDIT:::

that won't work, do this

sudo chown -R root:root foldername

then 

sudo chmod -R 755 foldername

another EDIT::

you will have to be root to write to this folder as well, I don't think there is a way for you to only have delete be a root operation

---

