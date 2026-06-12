---
title: "Search"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by brander on 2007-03-06
When I search for a file, it only seems to look in the current folder. How can I get it to search sub-folders or the whole computer?

---

### Post by raja on 2007-03-06
There are multiple ways to search for files. Can you tell us more clearly what exactly you are doing. For a utility like google desktop search to index and quickly search all your files, you should also try out beagle.

---

### Post by brander on 2007-03-07
Hi, it was quite simple that I found out this, I wanted to edit fstab but couldn`t remember where it was.  The search turned up nothing so I saw that it only looked in the current folder. (Found fstab manually - very tedious).

There must be something better than this and I`ll try what you suggest.

---

### Post by bapoumba on 2007-03-07
In CLI (may not be what you are looking for):
```
:~ $ locate fstab
**/etc/fstab**
/etc/fstab.pre-uuid
/usr/share/doc/mount/examples/fstab.gz
/usr/share/doc/util-linux/examples/fstab.example2.gz
/usr/share/doc/Debian/reference/examples/fstab
/usr/share/man/man5/fstab.5.gz
/usr/share/vim/vim70/syntax/fstab.vim
/usr/share/gnome/help/desktopguide/sample/fstab_automountnetworkfoldersall
/usr/share/gnome/help/desktopguide/sample/fstab_automountfat
/usr/share/gnome/help/desktopguide/sample/fstab_automountnetworkfolders
/usr/share/gnome/help/desktopguide/sample/fstab_automountntfs

```

---

### Post by annda on 2007-03-07
search programs executed by a user look for files which belong to the user (default: your home directory). for originally network systems like unix/linux this is a very good idea - you wouldn't want other people to search through your files, right? the idea is that system files belong to the administrator, and users' files belong to users.

if you are not afraid of the command line, do this:

```
sudo updatedb
find name_of_file
```
or even more comprehensive:
```
locate name_of_file
```
( also after sudo updatedb - you will get the mot current info).

p.s. you can add directories to be searched in beagle's preferences, but i'm almost sure that user's permissions will prevent you from snooping in files that are not yours (you have the rights of an administrator/root BUT you are not root).

---

### Post by brander on 2007-03-08
Thanks, I`ll try those later. The computer is only used by me so all the files are mine(or should be).

---

### Post by brander on 2007-03-08
That is great. The locate command worked well but the find one did not find anything, I assume that only looks in the personal folders.
I have no aversion to using the command line and have masses of bat files in windows to do the things I want but a change to Linux commands take a bit of learning. Thanks for the help.

---

### Post by yigal.weinstein on 2007-03-09
find is a much more complex beast.  It can do much much more than locate.  

find can locate certain sized files, date modified files, etc. etc.

to use it to find something with a particular name use something like 

```
find /etc -name  'fstab'
/etc/fstab
find: /etc/cups/ssl: Permission denied
find: /etc/ssl/private: Permission denied
find: /etc/firestarter/inbound: Permission denied
find: /etc/firestarter/outbound: Permission denied

```

note the find command will not be able to find files you as a use do not have permission to access.  This is not true of locate as it is using a database which can be update by root.

---

### Post by yigal.weinstein on 2007-03-09
A way of using find without getting 100+ lines of permission denied at you is pipe all of the error messages out of your system.

```
find / -name fstab 2> /dev/null
/etc/fstab

```

but it will keep looking on your entire hd.  It is actually pretty neat but very different than locate.

---

### Post by igknighted on 2007-03-09
personally I like slocate, but I don't know if its in the default install

---

### Post by yigal.weinstein on 2007-03-09
Yes, it is.

---

### Post by kafkaian on 2007-03-13
What are people using to find files containing required text within the content of the file (not the file name)?

---

### Post by raja on 2007-03-13
> **kafkaian said:**
> What are people using to find files containing required text within the content of the file (not the file name)?

```
grep "text to search" /folder/with/files/*
```

Also you can use beagle or tracker if you have feisty to index not only text files but pdfs and so on.

---

### Post by kafkaian on 2007-03-13
Excellent, thanks Raja

---

