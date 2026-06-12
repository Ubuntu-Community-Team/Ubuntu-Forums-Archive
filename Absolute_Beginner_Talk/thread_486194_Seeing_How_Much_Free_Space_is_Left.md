---
title: "Seeing How Much Free Space is Left"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Matuku on 2007-06-27
This may seem like a silly question but how do I see how much free space is left on my hard drive in linux (in windows it was a simple question of selecting the drive and clicking properties but in my Ubuntu whilst that works for my other partitions it doesn't work for my "Filesystem" (the ext3) partition; any reason why?)

---

### Post by moore.bryan on 2007-06-27
*open a terminal and type ```
df
```*

---

### Post by mlentink on 2007-06-27
System>Administration>System Monitor>Filesystem

---

### Post by jfinkels on 2007-06-27
> **Matuku said:**
> This may seem like a silly question but how do I see how much free space is left on my hard drive in linux (in windows it was a simple question of selecting the drive and clicking properties but in my Ubuntu whilst that works for my other partitions it doesn't work for my "Filesystem" (the ext3) partition; any reason why?)

Open a terminal and enter:```
df .
```to see the free disk space on the current partition

OR

Press Alt+F2 and type ```
baobab
``` for a GUI

---

### Post by xelnaga666 on 2007-06-27
Just thought id mention if you would like a 'human' readable output in df, use the -h switch
```

df -h

```

---

### Post by moore.bryan on 2007-06-27
> **xelnaga666 said:**
> Just thought id mention if you would like a 'human' readable output in df, use the -h switch
```

df -h

```
*excellent addition... i never knew this option existed! :-)*

---

### Post by robertc36 on 2007-06-27
It is written in the bottom left hand corner of your home folder, or relevant folder for other drives,

---

### Post by speaker219 on 2007-06-27
Also, Applications > Accessories > Disk Usage Analyzer is nice, it will tell you what files/ folders are taking up the most space.

---

