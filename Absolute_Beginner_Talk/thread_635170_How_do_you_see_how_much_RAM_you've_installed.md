---
title: "How do you see how much RAM you've installed"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by inktri on 2007-12-08
I just want to make sure Ubuntu is detecting all of my memory

Thanks!

---

### Post by taurus on 2007-12-08
Applications -> Accessories -> Terminal
```
free
```

---

### Post by perce on 2007-12-08
in a terminal:

cat /proc/meminfo

---

### Post by spiderbatdad on 2007-12-08
you can do: Applications--> System--> Administration--> System Monitor. click resources tab

---

### Post by Mramius on 2007-12-08
Anyway to make those more human readable, using MB and GB?

---

### Post by crimesaucer on 2007-12-08
> **taurus said:**
> Applications -> Accessories -> Terminal
```
free
```

For megabytes, I like:

```
free -m
```


I also like to run a .conkyrc file to monitor all of my system stats: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by spai on 2007-12-08
[I am not the original poster but I had the same question and want to learn Linux:)]
Hmm actually I tried ¨free -m¨, it showed
```
srikanth@ubuntu:~$ free -m
              total       used       free     shared    buffers     cached
Mem:          1201        729        472          0        123        351
-/+ buffers/cache:        254        947
Swap:          454          0        454
```
Whereas system monitor shows 254 out of 1201, this mostly means system monitor shows the ¨-/+ buffers/cache¨ thing, right?

So I am curious now,
What does 729 used memory mean? What is -/+ buffers/cache?
And is my RAM usage related to -/+ buffers/cache?

---

### Post by crimesaucer on 2007-12-08
> **spai said:**
> [I am not the original poster but I had the same question and want to learn Linux:)]
Hmm actually I tried ¨free -m¨, it showed
```
srikanth@ubuntu:~$ free -m
              total       used       free     shared    buffers     cached
Mem:          1201        729        472          0        123        351
-/+ buffers/cache:        254        947
Swap:          454          0        454
```
Whereas system monitor shows 254 out of 1201, this mostly means system monitor shows the ¨-/+ buffers/cache¨ thing, right?

So I am curious now,
What does 729 used memory mean? What is -/+ buffers/cache?
And is my RAM usage related to -/+ buffers/cache?


123+351=474+254=728 is buffer + cache + used = total used ram of all apps running, including buffer and cache of old ram.

1201-254=947 is available ram - used ram = available free ram, including the buffer and cache as free ram ready to be dropped for any new ram space needed.

---

### Post by CatKiller on 2007-12-08
> **perce said:**
> in a terminal:

cat /proc/meminfo

++

---

### Post by spai on 2007-12-08
> **crimesaucer said:**
> 123+351=474+254=728 is buffer + cache + used = total used ram of all apps running, including buffer and cache of old ram.

1201-254=947 is available ram - used ram = available free ram, including the buffer and cache as free ram ready to be dropped for any new ram space needed.


I was confused at first, thinking that `free` command is incosistent with `system monitor`
Ya I understand it clearly now. 
Thanks a lot :smile:

---

### Post by crimesaucer on 2007-12-09
> **spai said:**
> I was confused at first, thinking that `free` command is incosistent with `system monitor`
Ya I understand it clearly now. 
Thanks a lot :smile:

No problem. 


@inktri- I also like the top command to see how each running process is affecting mem. Plus it also has the stats for: total-ram/ram-used/free-ram/cache/buffers/swap-total/swap-used/swap-free

```
top
```

to quit it press q:

```
q
```

---

