---
title: "Help freeing up disk space.."
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by dermotti on 2006-03-12
Im trying to trim the fat on my Ubuntu system and free up some disk space. My system right now is 8 gigs total (200megs of data that cant be deleted).

So what im wondering is, is there some easy way to find temp files and delete them?

And is there a way to display all the programs i have installed and see how much disk space they are taking up, so i can decide if i want to uninstall certain apps that are taking up significant space?

Ide like to get my system down to 4 gigs somehow....It will make my full system backups go much faster.

---

### Post by knalle on 2006-03-12
usually there arent that much temp files on linux, apt-get on the other hand has a large cache, 

these can be safely removed if you are online all the time,

```
du -m /var/cache/apt/archives/
```

also check the size of the system log

```
du -m /var/log/
```

these can be safely removed,

and ofcourse , clean your home dir and use synaptic to remove unwanted packages :-)

---

### Post by dermotti on 2006-03-12
Well the issue is Ide like to see the "size" of the package before i remove it, do decide whether it will make a signicant impact on my system. If the file is too small its not worth the risk of breaking something i actually use...

---

### Post by knalle on 2006-03-12
[QUOTE=dermotti]Well the issue is Ide like to see the "size" of the package before i remove it[/QUOTE]

you can see that in **synaptic**

---

### Post by dermotti on 2006-03-12
You are correct.... i guess i was not seeing it because the column was hidden and sorted to files that did not have a side. Thanks for your help!

---

