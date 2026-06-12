---
title: "Remove GoogleEarth"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by bigal1932flying on 2007-09-08
I have installed the latest version of GoogleEarth. How do I remove the old version?
I believe I installed the original with the command
"chmod 755 GoogleEarthLinux.bin" then
"./GoogleEarthLinux.bin"

---

### Post by Ek0nomik on 2007-09-08
Do you have a README file with Google Earth?  It should tell you how to remove the software in it.

If not, this is simply a guess as to what it will require to remove it (navigate to the directory of the contents):

```
make uninstall
make distclean
```

---

