---
title: "Problem Installing"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by Squizz on 2007-12-05
I'm trying to install a file but getting an error - this happens with a few packages, what am I doing wrong?

```

simon@simonubuntu:~/Desktop/qflash-0.1-bin$ sudo sh install-sh
Password:
mkdir: cannot create directory `/usr/share/qflash': File exists
mkdir: cannot create directory `/usr/share/libming/fonts': No such file or directory
cp: target `/usr/share/libming/fonts/' is not a directory: No such file or directory

```

---

### Post by ItsMitsHere on 2007-12-05
Why don't you try to install via apt-get or aptitude?

You can do it by typing **sudo apt-get install qflash** provided qflash is the shell name of the program you are trying to install and you are connected to the repository via internet. (repository is a large database storing lots and lots of programs!)

---

### Post by Squizz on 2007-12-05
```

simon@simonubuntu:~$ sudo apt-get install qflash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package qflash
simon@simonubuntu:~$ sudo aptitude install qflash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "qflash"
The following packages have been kept back:
  tzdata 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

It didn't seem to like that very much.  The syntax was exactly as it said in the install file, so it would seem that permissions of some sort are not correct on my machine.

---

### Post by asmiller-ke6seh on 2007-12-05
Try looking in the New Ubuntu User's Resource under the subject(s) dealing with Installation.

My guess is that you are a Linux user (Red Hat? Fedora?) that does not use the Debian Respository installation method. It's quite different, and you have to forget the notions you have learned about software installation.

See if this information (link is in my SIG, below) helps orient you.

---

