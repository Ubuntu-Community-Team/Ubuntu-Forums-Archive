---
title: "The new created file's default permission in the file manager(nautilus)"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by NeoRc on 2006-07-23
When I create a new file under the Shell, the default file permission is 644:
```
# touch file_name
```
But when I create a file in the file manager(nautilus), the default file permission is 600. Can I change it?

---

### Post by simonn on 2006-07-23
Looks like this is a bug in gnome-vfs

[http://bugzilla.gnome.org/show_bug.cgi?id=327249](http://bugzilla.gnome.org/show_bug.cgi?id=327249)

---

### Post by NeoRc on 2006-07-23
How to fix it?

---

### Post by aysiu on 2006-07-23
Have you tried [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9)?

---

### Post by NeoRc on 2006-07-23
> **aysiu said:**
> Have you tried [this](http://www.ubuntuforums.org/showpost.php?p=832721&postcount=9)?

I have download the acl from rep, and run the command:
```
# getfacl /home/neo
getfacl: Removing leading '/' from absolute path names
# file: home/neo
# owner: neo
# group: neo
user::rwx
group::r-x
other::r-x
```

---

### Post by simonn on 2006-07-23
Am I missing something or will right click -> Propeties -> Permissions or the chmod command not do the trick?

---

### Post by dabear on 2006-07-23
> **simonn said:**
> Am I missing something or will right click -> Propeties -> Permissions or the chmod command not do the trick?
You are missing something :D
But seriously, this is about the default behaviour for file creation in nautilus. Offcourse you could change the rights afterwards, but that's kinda annoying to do each freakin' time :)

This is particulary true when in /var/www and creating .php-files, only to find that the web server running as "www-data" or "nobody" can't read your file before you chmod them. 

edit:You could always make a  file chmoded the way you like it and place it in nautilus' template dir. Then you could just right click and select the file from the 'create new file' or similar though...

---

