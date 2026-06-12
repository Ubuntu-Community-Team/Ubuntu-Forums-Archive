---
title: "Ignore this post"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by Tortanick on 2006-06-21
I was wandering how to share a folder and its contents (preffrably includeing subfolders) with diffrent users on the same computer.

Prefrably a POSIX rather than Ubuntu method

---

### Post by briguy on 2006-06-21
The easiest way I can think of is to modify the directory and its files so that others can view / modify files as required using chmod, then linking with ln -s in the sharers home directories.

---

### Post by Tortanick on 2006-06-21
That link to everyone's home directory or just the owners?

---

### Post by x64Jimbo on 2006-06-21
It will link to everyone's directory that you put it in. Once you create that share and give it the correct permissions restrictions, it will be available to any user who wants to map to it. You could write a special login script that you have each user run that automatically maps the share to a subdirectory of their home directory.

---

### Post by Tortanick on 2006-06-21
Thanks both of you :)

---

