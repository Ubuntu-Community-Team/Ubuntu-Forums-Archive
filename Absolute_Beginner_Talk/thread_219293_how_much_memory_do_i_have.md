---
title: "how much memory do i have"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-07-19
hi; just installed a new memory card- is there a shell command that will show whether it's present?

thanks.
-steve

---

### Post by T700 on 2006-07-19
```
sudo lshw
```

Paul

---

### Post by Landoln on 2006-07-19
```
free -m
``` will show you the memory usage in your system in megabytes.  
top is another useful command, which shows you a summary of your system resource use.

---

### Post by editrix on 2006-07-20
I'm supposed to have 256 MB of memory, but sudo lshw says:

*-memory
          description: System memory
          physical id: 1
          size: 223MB

and free -m says:

             total       used       free     shared    buffers     cached
Mem:           218        213          4          0          1         74

Is this normal, or is the system not accessing all the memory it could?

---

