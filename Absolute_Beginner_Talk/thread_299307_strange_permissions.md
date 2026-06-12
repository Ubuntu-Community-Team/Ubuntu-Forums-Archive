---
title: "strange permissions"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-11-13
I just installed linux for the first time on my pc and I am getting frustrated with a permissions issue. Whenever I download a program, (ie JDK w/Netbeans), it saves it to my Desktop. From that point, I usually move it to my /home/root/ to be set up for all users. Anyway, if I try 'sudo sh progname.bin', it says 'blahblaah: No permissions' or something like that. Then, I type 'sudo chmod 775 filename' and wham-o, it runs. Why does this keep happening??

---

### Post by CatKiller on 2006-11-13
Because it needs to be executable before you can execute it.

---

### Post by cyris| on 2006-11-14
What you are looking to change is the default umask. I believe the default for files is 022.

[https://lists.ubuntu.com/archives/kubuntu-users/2006-April/004775.html](https://lists.ubuntu.com/archives/kubuntu-users/2006-April/004775.html)

check that article out. hope that helps :D

---

### Post by IYY on 2006-11-14
An easier way to make a file executable is

```
chmod +x filename
```

The effect will be the same, but it will preserve whatever other permissions were set on it before.

---

