---
title: "Permission Assistance"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-02-13
Hi.
I have a folder on my desktop full of delimited text files (all ending in .txt).  They are separated into subfolders.  I would like to set the permissions to only be Read access.  When I take away Execute permission, the folders can no longer be browsed with nautilus, so I guess I need to leave Execute permission.  I changed the permissions of each subfolder to include execute, but left the files with only read.  Here is my real problem however.

I used "sudo chmod -R 444 /mypath/folder" to change all the permissions at once.  However, can anyone explain this:
> user> ls -lt /home/levi/Desktop/athens
total 0
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/1998
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/1999
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2000
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2001
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2002
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2002-1998-land-comm
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2003
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2004
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2005
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/2006
?--------- ? ? ? ?                ? /home/levi/Desktop/athens/readme.txt
user> sudo ls -lt /home/levi/Desktop/athens
total 932
dr-xr-xr-x 2 levi levi 106496 2007-02-13 15:08 2002
dr-xr-xr-x 2 levi levi  16384 2007-02-08 12:48 1998
dr-xr-xr-x 2 levi levi  36864 2007-02-08 12:48 1999
dr-xr-xr-x 2 levi levi  36864 2007-02-08 12:48 2000
dr-xr-xr-x 2 levi levi  49152 2007-02-08 12:48 2001
dr-xr-xr-x 2 levi levi  24576 2007-02-08 12:48 2002-1998-land-comm
dr-xr-xr-x 2 levi levi 143360 2007-02-08 12:48 2003
dr-xr-xr-x 2 levi levi 143360 2007-02-08 12:48 2004
dr-xr-xr-x 2 levi levi 159744 2007-02-08 12:48 2005
dr-xr-xr-x 2 levi levi 212992 2007-02-08 12:48 2006
-r--r--r-- 1 levi levi    739 2007-02-08 12:33 readme.txt
user>


sudo can see the permissions and regular user levi cannot.  why is this?  If I am doing something wrong, please tell me how to give all users the ability to browse folders, but only read the files.

---

### Post by Bachstelze on 2007-02-13
```
sudo chown -R root:root /home/levi/Desktop/athens
sudo chmod -R 755 /home/levi/Desktop/athens
```

Will give all users read-only access to /home/levi/Desktop/athens and everything that's in it. root will still have write access of course.

---

### Post by l951b951 on 2007-02-13
That worked 90%.  One of the subfolders won't open in nautilus.  It says access denied.  However, all the rest open.  and if I run "gksudo nautilus" I can browse in it.  Ideas?

---

### Post by Bachstelze on 2007-02-13
could you please paste the output of *ls -l* on that folder ?

---

### Post by l951b951 on 2007-02-13
> **HymnToLife said:**
> could you please paste the output of *ls -l* on that folder ?

Here is my output.  The offending folder is 1998

> 
user> ls -l /home/levi/Desktop/athens/
total 932
drwxr-xr-x 2 root root  16384 2007-02-08 12:48 1998
drwxr-xr-x 2 root root  36864 2007-02-08 12:48 1999
drwxr-xr-x 2 root root  36864 2007-02-08 12:48 2000
drwxr-xr-x 2 root root  49152 2007-02-08 12:48 2001
drwxr-xr-x 2 root root 106496 2007-02-13 15:08 2002
drwxr-xr-x 2 root root  24576 2007-02-08 12:48 2002-1998-land-comm
drwxr-xr-x 2 root root 143360 2007-02-08 12:48 2003
drwxr-xr-x 2 root root 143360 2007-02-08 12:48 2004
drwxr-xr-x 2 root root 159744 2007-02-08 12:48 2005
drwxr-xr-x 2 root root 212992 2007-02-08 12:48 2006
-rwxr-xr-x 1 root root    739 2007-02-08 12:33 readme.txt


It may just be a nautilus thing, because i can navigate into the folder from the terminal.

---

### Post by l951b951 on 2007-02-13
Guess what?  A restart cured my problem.  Apparently nautilus just hung on to the old permissions.  Rebooted, and everything works.

---

