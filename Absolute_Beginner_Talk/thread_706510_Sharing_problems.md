---
title: "Sharing problems"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by wsetchell on 2008-02-24
So yesterday I made the switch from XP to Ubuntu 7.10.  I'm trying to make it so all users can access all the pictures of the other users.  What I've been trying is:

right click on the folder I want shared, select properties, select sharing, then at the bottom there is a box marked other users can run these files, and I make that into a check mark (like the instructions say), and I apply to sub-folders.  Finally I click okay.  When I go back to properties it looks exactly as it was before I changed the settings.  What is going on/ how can I fix this?

---

### Post by bilge.tutak on 2008-02-24
Check your parent directory permissions. Also give permission for reading, not running.

---

### Post by wsetchell on 2008-02-24
How can I check that?

---

### Post by bilge.tutak on 2008-02-28
you can look at the permissions for the parent folder from the properties of you can do
```
 ls -la 
```
in the folder and look at the permissions there.
You should see something like this
```

drwx------  9 file_user file_group 4096 Sep 11 10:54 backup

```
For a greater understanding search for file permission tutorials. It is an important issue.
However basically, 

d: directory
rwx(read/write/execute permissions) for file owner
--- (again read/write/execute) for group
--- (again read/write/execute) for others 
So for others to be able to read/access to your files you should have a permission something like
drwxr--r-- or drwxr-xr-x
which you can obtain by

```
chmod 755 -R your_folder 
```
It will recursively give read/execute permission to all of your files in a folder.
Be careful where to use this command, since it is giving read access to other users.

---

### Post by Oldsoldier2003 on 2008-02-28
> **bilge.tutak said:**
> you can look at the permissions for the parent folder from the properties of you can do
```
 ls -la 
```
in the folder and look at the permissions there.
You should see something like this
```

drwx------  9 file_user file_group 4096 Sep 11 10:54 backup

```
For a greater understanding search for file permission tutorials. It is an important issue.
However basically, 

d: directory
rwx(read/write/execute permissions) for file owner
--- (again read/write/execute) for group
--- (again read/write/execute) for others 
So for others to be able to read/access to your files you should have a permission something like
drwxr--r-- or drwxr-xr-x
which you can obtain by

```
chmod 755 -R your_folder 
```
It will recursively give read/execute permission to all of your files in a folder.
Be careful where to use this command, since it is giving read access to other users.

I wouldn't think that in the is case he would want to give write or execute  to others (public) so the least permissive permission that would allow the others group to see the pics would be 754...( unless i'm missing something here ? )

---

