---
title: "[SOLVED] Read only DVD-R"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Tabenx on 2008-01-27
I couldn't seem to find someone else with my exact problem so here it goes. I have some files on a DVD-R disk but I can't get them off due to permission difficulties. So, I decided to try gksudo nautilus, then locate to the DVD directory and change permissions, so I moved them to the root desktop and changed permissions there. Then, when I tried to move them to my music folder, it gave me the permissions error again even though the permissions were changed successfully. Please help!

---

### Post by taurus on 2008-01-27
Instead of moving them to root's desktop, why not move those files to your own directory and then change the ownership of those files from root to your login name so you can do whatever you want with them.

---

### Post by Tabenx on 2008-01-27
It doesn't let me do that, it wont let me move them from the DVD to my directory.

---

### Post by taurus on 2008-01-27
When you use "gksudo nautilus", instead of copying them to root, why not just copying them to your own $HOME directory or wherever you want them.  Then, change the ownership of those files.

Otherwise, can you post the content of your DVD to see what kind of permissions do those files have.  Normally, you should have read and execute to those files?

```
ls -la /media/cdrom0
```
Assuming your DVD is mounted to /media/cdrom0.

---

### Post by Tabenx on 2008-01-27
Sorry i was away.
tabenx@darkstar:~$ ls -la /media/cdrom0
total 8
drwxr-xr-x 2 root root 2048 2008-01-13 18:51 .
drwxr-xr-x 5 root root 4096 2008-01-27 13:05 ..
drwxr-xr-x 2 root root 2048 2008-01-13 18:51 Documents
---------------------
I tried to move them to my own home directory but it said i don't have proper permissions to do that, even when root.

---

### Post by taurus on 2008-01-27
```
ls -la /media/cdrom0/Documents
```
You cannot move files from CD-R to your harddrive because those files cannot be removed.  Therefore, you need to _copy_ them from the CD to your harddrive.

---

### Post by Tabenx on 2008-01-27
It said it cannot be copied because I don't have permissions to read it(I tried it as root as well, same result).

---

### Post by taurus on 2008-01-27
Do you get any error message when you ran the command in my previous post?

---

