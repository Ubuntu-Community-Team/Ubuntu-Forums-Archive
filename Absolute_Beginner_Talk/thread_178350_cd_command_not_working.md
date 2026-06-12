---
title: "cd command not working"
date: 2006-05-17
forum: Absolute Beginner Talk
---

### Post by ftnalex on 2006-05-17
Hi all,

Maybe I'm doing something wrong here.  I've tried to install several apps (wine, fuse, etc) and I keep hitting the same wall.  Here's a cut-and-paste of what I'm getting in my terminal window:
root@ubuntu:/home/jason# cd fuse
bash: cd: fuse: No such file or directory
root@ubuntu:/home/jason# cd desktop
bash: cd: desktop: No such file or directory

Now I know there's a Desktop folder under my profile and there's also a Fuse folder on the desktop and also in my home directory.  So what am I missing?

---

### Post by kabus on 2006-05-17
Filenames in Linux are case-sensitive. Try 'cd Desktop'.

---

### Post by Iowan on 2006-05-17
You might try **ls -a** to verify the directories are there.  If so, you could **cd ..** to verify the **cd** command is working.

---

### Post by ftnalex on 2006-05-17
Yep, tried that as well.  Still not working.

---

### Post by glotz on 2006-05-17
Type in ls -a, what do you get?

---

