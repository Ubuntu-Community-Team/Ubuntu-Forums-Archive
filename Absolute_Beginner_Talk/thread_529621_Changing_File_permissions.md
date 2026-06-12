---
title: "Changing File permissions"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by nanogeek on 2007-08-19
Hi:

I installed Edgy on an old pentium II machine with a 6gb hard drive.
I now resurrected an old 20gb hard drive (with I believe a bad MBR), reformatted it and mounted it successfully following the excellent direwctions at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
but I am stuck at the last step.
I granted permission to one user to use the new drive, but I would liek to grant all users read/write/delete access to all files on the drive.

I thought I did the following:
Using System->Admin->Users and groups
I opened Manage groups and opened the properties for the group called users
I checked all the users in the list. It was my intentiuon to all users (root, admin, harry) to the group users

then in terminal I ran:
sudo chgrp users  /media/mynewdrive
sudo chmod g+w /media/mynewdrive
sudo chmod +t /media/mynewdrive

This did not give me read/write access I was looking to establish

I still lack a fundamental grasp of users and permissions.
the CLI is still very foreign.
I want everyone to be able to use this drive.
Can someone please help me out?

TIA
nanogeek

---

### Post by Hobo Joe on 2007-08-19
Press ALT + F2, and it will give you a run prompt. Type 'gksudo nautilus', this will give you the file browse with root permissions.

Then navigate to the files/folders you want to have permission to, and right click on them and press properties, then press permissions, and set your username to 'create and delete files' permission.

That should do the trick.

---

### Post by nanogeek on 2007-08-19
Thanks for the tip.
this worked fine for setting my permissions, but I want to give all users permission.
I set "others" to "create and delete files" as well, but when I log in as another user, it denies me access in the child directories and shows the subdirectory icon with a lock on it.
How do I grant access to all users in all subdirectories too?

nanogeek

---

### Post by Hobo Joe on 2007-08-19
Are all the other users set as administrators?

To set subdirectories(I think) you just press the button that says 'set permissions to enclosed files'.

---

### Post by nanogeek on 2007-08-19
No, only admin is an administrator. POU is a plain old user.
I generally log in as POU, and use admin as a login only for admin stuff. 
I understood this was the proper way to use Linux.
I do want to grant POU and admin full right to the entire disk.

---

### Post by jamvegan on 2007-08-19
This might help:
```
sudo chgrp -R users /media/mynewdrive
```
Note the "-R", which means to recursively change the group on files and directories within the one you give as an argument.

I think that the instructions that you were originally following assumed that the new drive was empty while you were installing it and setting it up, and therefor there would be no need for the recursive option.

---

### Post by nanogeek on 2007-08-19
OK that did it.
I thought I had used the -R flag.
I must have had something wrong with the syntax.


TTFN

---

### Post by Hobo Joe on 2007-08-19
If you go to Users and Groups and check the properties of the users, there is a list of adminstrative options that you can select, so yes, it is possible to have two adminstrators.

---

### Post by deserthowler on 2007-08-19
From what I understand, :confused: you are having trouble navigating directories.  To navigate a directory you must have execute permission too.

Earl

---

