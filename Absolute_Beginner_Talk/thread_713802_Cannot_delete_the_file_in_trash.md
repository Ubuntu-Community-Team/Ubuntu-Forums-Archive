---
title: "Cannot delete the file in trash"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by adi_das on 2008-03-03
I Cannot delete the file in trash. See the screenshot. how to delete the file?

---

### Post by FreewareFan on 2008-03-03
Open a terminal and enter 

sudo rm -rf [the path to your file]


That should do it for you.

---

### Post by oedha on 2008-03-03
i suggest :
open terminal
cd /home/user_name/.Trash
sudo rm -Rf folder/filename

---

### Post by warbird on 2008-03-03
Or you can change the premissions on the file/folder in question:
open terminal
cd .Trash
ls -alR
(-a = all, including hidden files, l = listing format, R = recursive, all subfolders)

you'll see a list of stuff similar to this:
drwxr-xr-x   4 user group      4096 2008-03-03 02:49 .Trash

There probably is a folder with "root root" as user and group. to change this to your own account, do this:

sudo chown -R user:user Foldername 
(actually, the second user is the group name, but its the same as the user in this case. -R makes it recursive.)

Now you should be able to empty the trash normally.

---

