---
title: "SU wont write to a file"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by sbuntu on 2006-06-17
I am trying install a package by including the pkg in the sources.list file but for some reasons it refuses to write to it even though i am logged in as super user.

anyone@athena:~$ su sbuntu
Password:
sbuntu@athena:/home/anyone$ cd /
sbuntu@athena:/$ cd etc
sbuntu@athena:/etc$ cd apt
sbuntu@athena:/etc/apt$ ls -lrt
total 32
drwxr-xr-x 2 root root 4096 2006-04-18 15:47 sources.list.d
-rw-r--r-- 1 root root 2381 2006-05-30 21:59 trusted.gpg~
-rw-r--r-- 1 root root 2393 2006-05-30 21:59 trusted.gpg
-rw------- 1 root root 1200 2006-05-30 21:59 trustdb.gpg
-rw------- 1 root root    0 2006-05-30 21:59 secring.gpg
-rw-r--r-- 1 root root   30 2006-06-09 21:00 apt.conf
drwxr-xr-x 2 root root 4096 2006-06-09 21:20 apt.conf.d
-rw-r--r-- 1 root root 1784 2006-06-10 17:04 sources.list.save
-rw-r--r-- 1 root root 1784 2006-06-10 17:04 sources.list
sbuntu@athena:/etc/apt$ vi sources.list

-- i make the changes here in vi.....


but when i try to save it... 

:wq!

it says..
"sources.list" E212: Can't open file for writing

I thought maybe there arent write permission to the file and therefore when i
tried giving it permission, it says


sbuntu@athena:/etc/apt$ chmod +x sources.list
chmod: changing permissions of `sources.list': Operation not permitted
sbuntu@athena:/etc/apt$

Please advise


Do i need to log out of normal user and log in as super user and then do the above changes ?

---

### Post by aysiu on 2006-06-17
Just type ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```

---

### Post by professor_chaos on 2006-06-17
the command "su" is switch user, so the user "sbuntu" is not the owner of the file, root is, and thats why you cant edit the file. 
The common way to do things as administrator is the user the command "su" without anything following (this requires you to enable the root account).

Or the prefered way is the use the command "sudo", like "sudo vi source.list". 
Check this page out for more info. [https://wiki.ubuntu.com/RootSudo?highlight=%28root%29](https://wiki.ubuntu.com/RootSudo?highlight=%28root%29)

---

### Post by catlett on 2006-06-17
follow chaos' guide. you are getting confused about superusers.they do not log in and become root. they invoke root priveleges by using sudo. a command by a superuser without sudo is just a comand (sudo means superuser do) 
If you are going to stay in ubuntu you have to get use to sudo or your going to get mixed up doing simple things. forget su. just login at the login as the username you made at install. that user is a superuser. when you want root priveleges just preface your commands with sudo. at the prompt for password enter your user password (i.e. the one you login with)

If you're determined to turn your ubuntu system back into debian you can create a root password by entering ```
sudo passwd root
``` you will be prompted for a unix password. enter your password of choice. you will be asked to enter it again. Enter it again and that's it. Now you can get a root terminal by entering su, then your unix/root pasword. Leave sbuntu out of this;)

---

