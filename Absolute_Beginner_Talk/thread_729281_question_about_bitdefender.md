---
title: "question about bitdefender"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by thungmail on 2008-03-19
hi 
I downloaded a package 
```

bdfe-1.1-0mdv.src.rpm 

```
and then I did the following in terminal
```

tuan@tuan:~$ sudo alien-i/home/tuan/Desktop/bdfe-1.1-0mdv.src.rpm
sudo: alien-i/home/tuan/Desktop/bdfe-1.1-0mdv.src.rpm: command not found
tuan@tuan:~$ sudo alien -i home/tuan/Desktop/bdfe-1.1-0mdv.src.rpm
File "home/tuan/Desktop/bdfe-1.1-0mdv.src.rpm" not found.
tuan@tuan:~$ sudo alien -i /home/tuan/Desktop/bdfe-1.1-0mdv.src.rpm
        dpkg --no-force-overwrite -i bdfe_1.1-1_i386.deb
Selecting previously deselected package bdfe.
(Reading database ... 107055 files and directories currently installed.)
Unpacking bdfe (from bdfe_1.1-1_i386.deb) ...
Setting up bdfe (1.1-1) ...

```

What should I do next to launch bitdefender. I did some reading but I am still lost....

---

### Post by logos34 on 2008-03-19
Type 

which <packagename>

to find the executable* to launch it.  (should be either in /usr/bin or /usr/local/bin, or somewhere in home).  On the other hand maybe it put an entry in the Applications menu.

*you may have to add permission to run it:

sudo chmod u+x /path/to/file

---

