---
title: "Help with getting Ark to open .rar files?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by morr on 2006-08-06
Hello, I'm a ubuntu user since today who would really appreciate some help. I have a .rar file that I want to open, and Ark is supposed to be able to do that if I install some command line something. Please please can somebody tell me how to get Ark to open .rar files?

---

### Post by freewaybear on 2006-08-06
sudo apt-get install unrar

That worked for me. Good luck.

---

### Post by newagelink on 2006-08-06
edit: nevermind, i found [http://ubuntuforums.org/showthread.php?t=224207&highlight=extracting+rar](http://ubuntuforums.org/showthread.php?t=224207&highlight=extracting+rar)

> **freewaybear said:**
> sudo apt-get install unrar

That worked for me. Good luck.Didn't work for me. :(
```
daniel@daniel-laptop:~$ sudo apt-get install unrar
Password:
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

```Help? I'm not familiar with this Ark program. I just right click on the file > "Extract Here" and it says "Could not open ... Archive type not supported."

---

### Post by geokok1981 on 2006-08-06
Have you enabled the rest of the available repositories (universe, multiverse) or do you have only the default ones activated?

If that is the case try activating them all and give it another go.

---

### Post by morr on 2006-08-08
Thanks, I got it working

---

