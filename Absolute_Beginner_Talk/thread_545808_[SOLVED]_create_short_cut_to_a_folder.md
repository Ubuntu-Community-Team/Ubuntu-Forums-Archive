---
title: "[SOLVED] create short cut to a folder"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by adityakavoor on 2007-09-08
how can  i create a shortcut to  a folder in my ntfs drive on the ubuntu desktop ???
pls help

---

### Post by banewman on 2007-09-08
Right click anywhere on the desktop, choose create launcher. Leave it at application, call it something(name), and for the command type "nautilus /sda1(if that is the windows folder) 
/path/to/file
e.g - " nautilus  /sda1/my documents/work/monday.txt.
Hope this helps. :)

---

### Post by MDSanta on 2007-09-08
theres probably a better way but thisis how I do it sorta...


right click on folder
create launcher
I choose applicaiton
give it a name

as for command I put
         nautilus /home/restofaddress

I created a hidden folder somewhere in the system and created a link like this on the desktop but made sure to put gksudo at the beggining of the command, so the contents are only viewable to room if opened through that link.


edit -
newman beat me to it :o

---

### Post by adityakavoor on 2007-09-08
noooo . i tried both methods ... none of those work on a directory (folder):confused:

---

### Post by runemaste644 on 2007-09-08
I think thats called a Symlink. Ill look around and post when i find out how to make one.

---

### Post by runemaste644 on 2007-09-08
Ive got it! Assume the folder you want to make a symlink of is named Folder
```
ln -s Folder
```
Thats how you symlink it!
Oh, and make sure you are in a different directory than the file is, like:
```
adityakavoor@laptop:~/Desktop$ ln -s /home/adityakavoor/Folder
```
That would make the symlink on your desktop.

---

### Post by Marat Galiev on 2007-09-08
What you problems?:)
first read
```
man ln
```
if you want create shortcut do this:
```
ln -s /media/ntfsdrive/ntfs-drive-folder /home/user/Desktop
```

---

### Post by adityakavoor on 2007-09-08
thank you....... runemaste644 and Marat Galiev :popcorn:

---

### Post by Seaker on 2007-09-13
The manual says the -s is for symbolic link.  So, what is the difference between a symbolic link and a hard link?

---

### Post by sloggerkhan on 2007-09-13
Out of curiosity, what is the reason that right clicking and hitting 'make link' doesn't work?

---

