---
title: "How to Monitor Memory Usage"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2007-06-17
I want to know, rougly, how much memory a month a process is using for when I buy a VPS. Can someone show me how to do this over the command line?

---

### Post by jonward0690 on 2007-06-17
free -mt

---

### Post by starcraft.man on 2007-06-17
> **Warpnow said:**
> I want to know, rougly, how much memory a month a process is using for when I buy a VPS. Can someone show me how to do this over the command line?

Can you be a bit more clear? By memory your referring to RAM usage yes? The easiest and quickest way is to just open up the system monitor (System > Administration > System monitor) (or TOP in the command line, sort memory with Shift + M) and look at the memory used either in total (resources tab) or the individual apps under processes. If you want an approximate average of RAM usage, load up all the apps you use most commonly and watch the RAM go up and see which apps are taking it all. I don't see why monthly RAM monitoring matters though it fluctuates based on what you do and snap shots at its peak easily tell you if you need more or are fine. If I didn't get what you meant please be a lil clearer... its usually best to give more and not less info.

Do you mean this [VPS]("http://en.wikipedia.org/wiki/Virtual_private_server") btw?

---

### Post by Warpnow on 2007-06-17
I currently run my text based game on a MUD host. Mud hosts monitor memory usage in Percents. I need to figure out, using the shell of my mud host, how much I'd end up using in megabytes, which is what a virtual private server uses, which I am considering switching to.

---

### Post by Warpnow on 2007-06-17
Someone told me that if I checked the RSS in the ps that was the ram, is that so?

---

### Post by pmg on 2007-06-18
The **RSS** field is the **resident set size**, or the process size of the process's data in real memory, meaning it excludes anything that has been paged out to swap space.  Take a look at the **SZ** and **VSZ** values from **ps**.  I think **VSZ** is what you want.  The man page for **ps** says it's:
>  virtual memory usage of entire process.
 vm_lib + vm_exe + vm_data + vm_stack
which would include the size of the executable, the libraries it's using, and all the data, statck and heap, including what's swapped out.

---

