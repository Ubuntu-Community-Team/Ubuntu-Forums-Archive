---
title: "How do I check what Kernel im using?"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-05-06
Not so long ago, I saw a command that show what kernel your system is using.
Now I cant find it :(

Does anyone know what that command is?

I compiled the latest kernel not so long ago, and have been using it ever since. But yesterday Ubuntu came with some updates, and one of them was a never kernel? 

Well, I would really love to get that command again, so I can check what kernel im using :)

Thanks

---

### Post by astoltz on 2006-05-06
I'm sure there are lots of ways - one is: ```
cat /proc/version
```

---

### Post by aktiwers on 2006-05-06
Thanks!

> aktiwers@ubuntu:~$ cat /proc/version
Linux version 2.6.16-cks4 (root@ubuntu) (gcc version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)) #1 Tue Apr 18 01:09:24 CEST 2006
aktiwers@ubuntu:~$


It worked! :)

---

### Post by ajack on 2006-05-06
[QUOTE=astoltz]I'm sure there are lots of ways - one is: ```
cat /proc/version
```[/QUOTE]

Another way is:

```

uname -r

```

---

### Post by patrick295767 on 2006-05-06
```
uname -a
```

---

### Post by ajack on 2006-05-10
[QUOTE=patrick295767]```
uname -a
```[/QUOTE]

I suggested the "-r" parameter as the original thread question was "How do I check what Kernel im using?" and it was obvious that the kernel type was Linux.  :mrgreen: 

The "-a" parameter will show everything that uname can report which is more than just kernel version.  :)

---

