---
title: "how to chmod certain filetypes in directory tree"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-11-13
Hi,

I'd like other users than myself and my group not to be able to view *.log files.
I have a directory with a lot of subdirectories and a lot of them include *.log files.
How can I (recursively?) chmod all *.log files at the same time?

Thanks!

---

### Post by Pumalite on 2007-11-13
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[http://ubuntuforums.org/showthread.php?t=589909](http://ubuntuforums.org/showthread.php?t=589909)

---

### Post by bartkl on 2007-11-13
I'm sorry, but I don't see the relevance of these articles. Well there is some relevance, but I need to know how I can use chmod combined with certain wildcards and parameters such that I can chmod one certain filetype over a directory tree.Other software is fine too.

---

### Post by K.Mandla on 2007-11-13
I believe chmod has an -R flag that recurses through subdirectories, so maybe something like ...

```
chmod -R 777 *.log
```
I just used 777 there as an example; change it to a+x,o+w or whatever you desire.

---

### Post by bartkl on 2007-11-13
```
bartkl@bartkl-desktop:~/Music$ sudo chmod -R 660 *.log
chmod: cannot access `*.log': No such file or directory
bartkl@bartkl-desktop:~/Music$ sudo chmod -R 660 ./*.log
chmod: cannot access `./*.log': No such file or directory
```

As you can see I also tried a variant. It doesn't work, too bad :(

---

### Post by Dr Small on 2007-11-13
Only use "*.log" if your files end in .log

---

### Post by bartkl on 2007-11-13
I did :)
At least the first time I did. In my code there's two attempts.

---

### Post by K.Mandla on 2007-11-13
I think you might have to step up one directory, and then use that as the prefix to the *.log wildcard. 

```
chmod -R 660 directory/*.log
```
I'm kind of guessing at this point, but it might work.

---

### Post by bartkl on 2007-11-13
```
bartkl@bartkl-desktop:~/Music$ cd ..
bartkl@bartkl-desktop:~$ sudo chmod -R 660 Music/*.log
chmod: cannot access `Music/*.log': No such file or directory
```

Doesn't seem to pull it off either.

---

### Post by bartkl on 2007-11-14
perhaps someone knows a tool that can help me out?
some gui or something.

---

