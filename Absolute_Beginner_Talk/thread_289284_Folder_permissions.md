---
title: "Folder permissions"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2006-10-30
Hi!!!!
I created folder using command in terminal: sudo mkdir down. Now I have folder down but root is file owner and I can't write in it, no copy, no direct download, cant delete it.....  How can I change that? How to set me for file owner???? Command in terminal???

---

### Post by blind0wl on 2006-10-30
first thing to do is find out what your user and group is to allow you access so do a

```
ls -al /home/
total 1
drwxr-xr-x  6 root     root    152 2006-08-10 16:38 .
drwxr-xr-x 27 root     root    784 2006-08-10 16:52 ..
drwxr-xr-x  3 dave     dave    240 2006-10-26 12:45 dave
```

see the dave, dave after the 3?  Thats my local user group.

so to change the folder's permissions on your machine you would need to run

```
sudo chown -R dave:dave /down
```

make sure you know the full path to your down directory and obviously substitue the dave to whatever you got out of the ls -al

If your confused just post the output of your ls -al /home/ and post where the down directory is and I'll give you the command.

For future reference, if you want to create a directory that you want access to, dont bother with the sudo, just mkdir from the prompt, ie.

```
mkdir /down
```

cheers

Blindy

---

### Post by nickburns on 2006-10-30
another easy way to do it is:

sudo chmod 777 -r /your/folder/

It will give all powerful rights to the folder and any subdirectories, and all the files in the folder, but it sounds like you folder is empty.

---

### Post by _mOrgoth_ on 2006-10-30
Thx!!!! :d

---

### Post by bodhi.zazen on 2006-10-30
> **nickburns said:**
> another easy way to do it is:

sudo chmod 777 -r /your/folder/

It will give all powerful rights to the folder and any subdirectories, and all the files in the folder, but it sounds like you folder is empty.

You need to sudo that if root is the owner of the directory.

See blind0wl's post.

---

