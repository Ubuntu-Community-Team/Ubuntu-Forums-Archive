---
title: "File-Folder Permissions"
date: 2006-02-03
forum: Absolute Beginner Talk
---

### Post by MaxDave on 2006-02-03
I need some help.  I copied a bunch of files from my NTFS windows drive onto my HD that I run ubuntu off of.  All files and flolders were copied as read only.  I need to move these files around.  But I am continously getting errors becasue of permissions.  I will set the parent folder as read write execute in properties, but it doesn't change any sub folders and files.  There are thousands of files that I need to reorganize.  What is the easiest way to change permissions all at once?  I have tried serching the forum but didn't find a clear awnser.

Thanks for your help.
David

---

### Post by Virogenesis on 2006-02-03
sudo chown -R <username> /folder/ <---- changes to ownership to your user
chmod -R g+rw  <--- changes files to read and write access

---

### Post by MaxDave on 2006-02-04
Thanks for the reply.  I tried the code and it didn't do what I was expecting.  It simply changed the read write permissins for the parent folder.  all sub folders and files remained read only.  I have thousands of files in in numerous sub folders.  I tried to delete them and i couldn't even do that because of all of the read only files.  I need a command that will allow me to change the permissions of all of the sub folders and files at once.  Or if I can delete the entire directory without having to send it to the trash would work as well.

Thanks

---

### Post by aysiu on 2006-02-04
NTFS is strictly read-only from Linux.
If you want read/write access, you should consider making a FAT32 partition to share files between Windows and Linux.

See the fourth link of my signature for more details.

---

### Post by MaxDave on 2006-02-04
[QUOTE=aysiu]NTFS is strictly read-only from Linux.
If you want read/write access, you should consider making a FAT32 partition to share files between Windows and Linux.

See the fourth link of my signature for more details.[/QUOTE]


Please read my first post.  I copied the files from an ntfs drive onto my ubunto partition.

---

### Post by aysiu on 2006-02-04
Sorry. Careless reading on my part.

Let's say the parent folder is /random_files, you'd use this command ```
sudo chmod -R 777 /random_files
```

---

### Post by MaxDave on 2006-02-04
Thanks a bunch! That worked.  I had tried that code from another post but apparently i typed something wrong because it worked this time.

Thanks

---

### Post by aysiu on 2006-02-04
Glad it worked out. Sorry I misread your first post.

---

### Post by gjohn2 on 2006-02-04
Hi,

I have a semi-similar problem, i have a folder in my trash and i can't delete it.
cause its not empty and something about permissions.

/home/hhhh...sheet.htm" cannot be deleted because you do not have permissions to modify its parent folder.

quoi is this about?

-gregor

---

