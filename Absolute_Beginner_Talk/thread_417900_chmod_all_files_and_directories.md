---
title: "chmod all files and directories"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by SodiumKPump on 2007-04-22
how do you chmod an entire directories contents, including all files and subdirectories etc without having to do each one individually?  thanks!

---

### Post by yabbadabbadont on 2007-04-22
To change the user:group of all files and directories in, and below, basedirectory:
```
chmod -R user:group basedirectory
```
You can use "-R" with chmod to set the permissions too, but you generally don't want to use the same permissions for files as you would for directories.  Most files should not be executable, but most directories should have the execute permission set.  In this situation, I use the "find" command with its "-type" and "-exec" options to run "chmod" with the correct permissions for each.  Example:
```
find basedirectory -type d -exec chmod a+rx {} \;
```
This will add read and execute permission to basedirectory and all sub-directories it contains.
```
find basedirectory -type f -exec chmod 644 {} \;
```
This will change the permissions of all files in and below basedirectory to 0644  (rw-r-r).
```
find basedirectory -type f -name "*.jpg" -exec chmod 600 {} \;
```
This will change the permissions of all files in and below basedirectory that have a ".jpg" extension to 0600.  (read/write for the user and not accessible by anyone else)

---

### Post by SodiumKPump on 2007-04-22
Thanks!

---

