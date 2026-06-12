---
title: "Multu-User query"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-09-17
Hi

I currently dual boot with XP and Ubuntu and have several partitions between two hard discs. I have my two kids as users on my machine but I wanted only certain partitions to be available to each of them. (Their own partitions and backup partitions) At the moment they have access to all partitions. Is there an easy way to do this?

Many thanks

gazzadtfan

---

### Post by jackocleebrown on 2007-09-17
Sure,

if you make the files on that partition belong to your user you can set the permissions so that only you can browse and view the files.

say you have the partition you want to restrict at "/media/hda1" and your user name is "myname" you can run this command "sudo chown myname -R /media/hda1" to change all files to be owned by you. Then you can change the access permissions so that only your user can browse, read and write the files in the partition like this "chmod  u=wrX,og-wrx -R /media/hda1". 

If you need to allow access to other users too you can do a similar thing but with group permissions (and add the permitted user to the group).


Jack.

---

