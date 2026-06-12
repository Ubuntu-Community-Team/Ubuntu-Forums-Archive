---
title: "error launching the application"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by Mark Bolton on 2005-08-26
There was an error launching the application.
Details: Failed to execute child process "/usr/bin/iPodder" (No such file or directory)
----------------------------------------------------------------
Apears when I try to run iPodder either from the command line or from the launcher I created. The file is described as a broken link and disapers when clickedupon.
---------------------------------------------------------------
[https://wiki.ubuntu.com/IPodder](https://wiki.ubuntu.com/IPodder) is where I got the instructions to progress this far.
---------------------------------------------------------------
mark@markubuntu:~$ /usr/bin/iPodder
bash: /usr/bin/iPodder: No such file or directory
mark@markubuntu:~$ sudo chmod 644 /opt/iPodder/ipodder/players.py
Password:
chmod: cannot access `/opt/iPodder/ipodder/players.py': No such file or directory
mark@markubuntu:~$
---------------------------------------------------------------

It seems clear that the install  has not completely occured. 

A little guidance would be greatly apreciated.

Kind Regards

---

### Post by amohanty on 2005-08-26
try at terminal:

locate -u
locate iPodder

or 

type iPodder

or 

cd /
find . -iname iPodder

Also AFAIK ubuntu does not create /opt by default. If you did not install iPodder as root via sudo /opt was probably not created. Try:

cd /opt
 and see what is there. Also at any point of time you can run the installer again. It will simply overwrite the files.

HTH
AM

---

