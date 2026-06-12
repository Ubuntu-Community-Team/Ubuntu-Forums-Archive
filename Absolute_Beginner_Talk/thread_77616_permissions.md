---
title: "permissions"
date: 2005-10-17
forum: Absolute Beginner Talk
---

### Post by likwid on 2005-10-17
I find that i can resolve problems i've been having with mounted file system access by changing the permissions for its contents. 

How can i set the permissions for the entire tree structure of a mounted drive? At the moment only the level i'm at is affected.

Thanks!

---

### Post by LHZ on 2005-10-17
Do you change permissions in the File Browser, or through the command line? In a terminal, typing 

chmod -R u+rwx \bla

should work (u+rwx being the permissions you want to set, \bla the directory you want to start in). The -R means 'recursive', telling chmod to continue in subdirectories.

If you use the file browser, I don't know how to do this. You might want to look around for a tutorial on how to use chmod from the command line, or post some questions here.
[http://www.linux.org/lessons/beginner/l14/lesson14b.html](http://www.linux.org/lessons/beginner/l14/lesson14b.html) has some info on chmod.

---

### Post by davmac on 2005-10-17
I think you need to specify the -R or --recursive option with chmod.

So the command "chmod -R 755 mydirectory" would set read and execute access for everyone and also write access for yourself for mydirectory and everything under it.

HTH,

Dave Mac

---

### Post by likwid on 2005-10-17
That's great. Thanks!

---

