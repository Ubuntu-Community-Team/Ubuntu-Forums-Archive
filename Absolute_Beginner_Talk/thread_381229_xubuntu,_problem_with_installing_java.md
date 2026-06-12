---
title: "xubuntu, problem with installing java"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by ahl on 2007-03-10
hello!

I have installet xubuntu 6.10 and tried to install sun java 5.0 runtime with the add/remove tool in det Application menu.

During install, everything look like it have stoped. And I rebootet the computer.

Now No Java is working. Inside the Add/remove tool, Java Runtime is marked as installed. I'm not able to remove it or to install Java Runtime again.

Is there anything I can do to completely remove it or to install it again ?

---

### Post by phossal on 2007-03-11
I recommend installing it using the .bin file directly from SUN. As for removing it, you might try:
```
sudo apt-get remove *package-name*
```

---

