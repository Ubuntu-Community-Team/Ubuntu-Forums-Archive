---
title: "Somehow I locked the home  folder ?"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by JParkus on 2007-08-16
Not sure what I did but most of the files and folders in my home folder have the lock on the icon . I have to sudo open cedega .I dont remember what I changed.

---

### Post by RaZer0r on 2007-08-16
check the permissions with ls -al /home
```

ls -al /home

```
if it sais your home folder is owned by root you can change that by doing:
```

sudo chown -R username:username /home/username

```

hope that helped.

---

### Post by mikeyphi on 2007-08-16
Check the ownership of the folders/files - right click select properties/permissions. Could be you created them as Root or as another User?

---

### Post by heimo on 2007-08-16
> **JParkus said:**
> Not sure what I did but most of the files and folders in my home folder have the lock on the icon . I have to sudo open cedega .I dont remember what I changed.

Those files are probably owned by another account / user. See file properties. You may need to run "sudo chown" on those files on terminal (I don't know GUI way to do it). Something like
```
sudo chown yourusername:yourusername filename.ext
```You can put -R after chown to make command recursive, and then use wildcards like asterisk * as a filename to change ownership of every file and directory in your home directory. DO NOT CHANGE OWNERSHIP OF OTHER FILES in your system, it'll ruin it.

EDIT: RaZer0r gave you good advice.

---

### Post by JParkus on 2007-08-16
i  did the chown command figured i would restart the computer and see how it worked .
It didnt work well its telling me i dont have permission and the read and write properties may need to be changed.

---

### Post by jfinkels on 2007-08-16
> **JParkus said:**
> i  did the chown command figured i would restart the computer and see how it worked .
It didnt work well its telling me i dont have permission and the read and write properties may need to be changed.

Post the output of this command:```
ls -l /home
```

---

### Post by JParkus on 2007-08-16
melissa@ubuntu:~$ ls -l /home
total 8
drwxr-xr-x 17 melissa melissa 4096 2007-08-16 21:50 melissa
dr-xr-xrwx 66 parkus  root    4096 2007-08-14 21:44 parkus
melissa@ubuntu:~$ 

I added my wife as a user so I could get in to the computer

---

### Post by jfinkels on 2007-08-16
> **JParkus said:**
> melissa@ubuntu:~$ ls -l /home
total 8
drwxr-xr-x 17 melissa melissa 4096 2007-08-16 21:50 melissa
dr-xr-xrwx 66 parkus  root    4096 2007-08-14 21:44 parkus
melissa@ubuntu:~$ 

I added my wife as a user so I could get in to the computer

Try this command:```
sudo chown parkus:parkus /home/parkus
```

It changes the owner of /home/parkus to 'parkus' and the group to which it belongs to 'parkus'.

Then do this:```
chmod 755 /home/parkus
```
This changes the mode (access rights) of the directory to read, write, and execute for the owner, read and execute for the group to which it belongs, and read and execute for all other users (I think that's the default for home folders).

---

### Post by JParkus on 2007-08-16
I added the recursive command now i get 

melissa@ubuntu:~$ ls -l /home
total 8
drwxr-xr-x 17 melissa melissa 4096 2007-08-16 22:08 melissa
dr-xr-xrwx 66 parkus  parkus  4096 2007-08-14 21:44 parkus
melissa@ubuntu:~$ 


but upon login I get an error with the files

home/.dmrc
/home/parkus/.ICEauthority

---

### Post by jfinkels on 2007-08-16
> **JParkus said:**
> I added the recursive command now i get 

melissa@ubuntu:~$ ls -l /home
total 8
drwxr-xr-x 17 melissa melissa 4096 2007-08-16 22:08 melissa
dr-xr-xrwx 66 parkus  parkus  4096 2007-08-14 21:44 parkus
melissa@ubuntu:~$ 


but upon login I get an error with the files

home/.dmrc
/home/parkus/.ICEauthority

Do this:```
chmod 755 /home/parkus
```

You should usually never do a recursive chmod or chown. You have now changed the permissions on those hidden files so something trying to access them is having problems.

EDIT: My .dmrc and .ICEauthority look like this have mode 600 .

---

### Post by JParkus on 2007-08-16
chmod 755 got me back in but there are still some locks on files . Now befor I start just playing around again what am supposed to do with those

---

### Post by JParkus on 2007-08-16
One instance is when I try to load WOW via Cedega I have to su in and then I get the error

parkus@ubuntu:~$ sudo cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
wine: '/home/parkus/.cedega/World of Warcraft/wineserver-ubuntu-root' is not owned by you


I dont want to own everything just what i did befor I noobed my puter

---

### Post by jfinkels on 2007-08-16
> **JParkus said:**
> One instance is when I try to load WOW via Cedega I have to su in and then I get the error

parkus@ubuntu:~$ sudo cedega
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
wine: '/home/parkus/.cedega/World of Warcraft/wineserver-ubuntu-root' is not owned by you


I dont want to own everything just what i did befor I noobed my puter

When you did 'chown -R foo:bar baz', you changed the ownership of all the subfolders and files under the directory 'baz'. I don't know if it's possible to undo those changes. You can try ```
chown parkus:parkus "/home/parkus/.cedega/World of Warcraft/wineserver-ubuntu-root"
```but I don't know if that will do anything for you. You may have to reinstall World of Warcraft...

---

### Post by JParkus on 2007-08-16
its not going to kill me is i have to so just chown ICE and cedega .works for me  thank you

---

### Post by gmanpsycho on 2007-08-31
I this is an old thread but I wanted to thank you all for the help. I noobed my HOME directory and this thread helped me out of a jam. Ubuntu Rocks!!!!:guitar:

---

