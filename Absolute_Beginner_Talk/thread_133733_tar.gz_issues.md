---
title: "tar.gz issues"
date: 2006-02-20
forum: Absolute Beginner Talk
---

### Post by thrakirr on 2006-02-20
I'm attempting to extract the ivtv program, into /usr/src. I've tried a variety of tags for "sudo tar", including -x, -v, -f, --gzip, and so on. Nothing has worked.. also, for some reason, I can't log on as root. I think I may have forgotten to set the root password, as sudo accepts my user login password. But anyway, any help on this tar ugliness would be greatly appreciated. Thanks in advance.

---

### Post by paxmaster on 2006-02-20
is a good idea to read the man pages 

the command is to extract  .tar.gz is = tar xvzf filename.tar.gz 

for example the tar file is in your home directory and you want to extract it to /usr/src 
just add the option -C and the directory you want the package to be extract

The directory /usr/src is drwxrwsr-x 3 root src 72 2006-02-19 23:14 /usr/src/
this means that root has the permission 
just do the command with sudo 

it is bad idea to set a password  with root account :)

---

### Post by nickle on 2006-02-20
Just remember that whatever the tar options you use the *f *must be the last before the file name...

---

