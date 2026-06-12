---
title: "delete directorys on portable media"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by fedex1993 on 2007-12-03
how can i remove folders like on my portable hardrive threw the terminal command

---

### Post by madamore on 2007-12-03
lets make an example:
$ mkdir test // creation of directory called test
$ rm -r test // elimination of test directory and its contents

Sow "rm -r directory" shout work properly if you have user or group rights to do it.

Remember, you can always do the following for help:
$ rm --help
$ man rm

good luck!

---

### Post by daimaru on 2007-12-03
what exactly are you asking here ? i mean you definately shoud not use the /home command but the one where your portable media is mounted and that would be under /media/yourdevice so
cd /media 
ls 
check what your portable device is mounted as and then cd to that device
cd /media/mydevice
then you can execute your rm command, but hey you will lose everything on the disk so make sure your in the right place. to check where your at you can use the "print working directory" command
```
pwd
```
that shows you where your at in the filesystem. 
good luck and don't blame me if you erase stuff you didnt want to because you where in the wrong directory. :)

---

