---
title: "Doom3 and ia32 libs"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by voidoid on 2007-05-13
Hi, got a double problem here, first I can't get ia32-libs to install on my amd64 system I just get this message ```
$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs
```

and secondly to install doom3 I need to use a run file, how do I do this? (might seem like a very noob question, but I am a complete noob!)

Ta.

---

### Post by josesanders on 2007-05-14
I'm not sure if that library is in the repos, but have you edited your /etc/apt/sources.list file to add extra repositories?  If not, you need to open that file and delete the '#' at the beginning of a couple of the lines, and add the word 'multiverse' at the end of the 'universe' line.  Then save the file and run the following command:
$ sudo apt-get update
Then, if the library is in the newly added repositories, you can run the command again to install it.  If you have already done that and you still can't find it, you can download it here:
[http://packages.ubuntulinux.org/feisty/libs/ia32-libs](http://packages.ubuntulinux.org/feisty/libs/ia32-libs)

For the .run file, I've never done it, but according to this thread:
[http://ubuntuforums.org/showthread.php?p=2645230](http://ubuntuforums.org/showthread.php?p=2645230)

all you have to do is change the permissions to make it executable:

$ sudo chmod 755 filename.run

Then run it:
$ sudo ./filename.run

---

