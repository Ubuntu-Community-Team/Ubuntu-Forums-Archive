---
title: "What is NICE ?"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by Alienkind on 2007-01-17
What is the term *nice* in relation to computer memory in Linux? Is this the same as or different from what is described when I type in

```
$ man nice
```

Also, I just upgraded my RAM from 512 MB to 2 GB and it seems that my memory usage has scaled up as well :-k . What's up here and why?

---

### Post by pay on 2007-01-17
nice is the priority that a program has where -20 is the highest and 19 is the lowest

---

### Post by IYY on 2007-01-17
> What is the term nice in relation to computer memory in Linux?

It's exactly what the man page says it is: a program to set the priority of processes. For example, you could use it to launch Audacity at top priority when doing heavy sound editing.

> Also, I just upgraded my RAM from 512 MB to 2 GB and it seems that my memory usage has scaled up as well  . What's up here and why?

Unix-like systems (and any other decent OS!) are able to take up the optimal amount of memory. If there is more memory to use, it will be used. Why have those megabytes sit there doing nothing?

---

### Post by Alienkind on 2007-01-18
Thanks for those posts. Now I'll be able to look up that *nice* on my own from here on. (BTW, how is the word pronounced? Does it like the adjective or like the city?)

Well, it makes perfect sense to know that Linux uses as much available memory as possible to get the most performance out of hardware that is already there. I did notice, shortly after my thread starter post, that ksysguard shows much of that extra used memory being used as cache memory. The default grid sensor for physical memory in ksysguard shows three plots: application memory, buffers, and cache. I understand that app mem is the memory used by the programs I have running, but what about the other two? What exactly are they?

---

### Post by weresheep on 2007-01-18
Hello,

This [page]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management") offers a pretty good explaination of linux memory management. As for the pronounciation of NICE, I've only ever heard it pronounced as in "Have a nice day" but I could be wrong.

-weresheep

---

### Post by mcduck on 2007-01-18
I'm pretty sure it's pronounced like the adjective. Anyway, it's telling how nice the program is towards other programs running on the machine..

Btw, you can also use nice to limit the resources users can have on the machine..

Cache is files from your hard disk stored in memory in case you want to access them again. It's about 1000 times faster to read them from memory than from hard disk, and if no application is using the memory it's better to use it for cache than just leave it unused.And buffers are just some read/write buffers for temporary storage of data, allowing smoother multitasking. For example disk writes are buffered and the actual writing happens when your system isn't doing anything more important (or when buffer gets full).

---

