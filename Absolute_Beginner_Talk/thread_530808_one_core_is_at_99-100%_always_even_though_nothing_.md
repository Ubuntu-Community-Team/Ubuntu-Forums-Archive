---
title: "one core is at 99-100% always even though nothing is running"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by legoman666 on 2007-08-20
I have tried the command "sudo rm -rf /etc/xdg/menus/debian-menu.menu" to fix it, however, one of my cores is still always at 100%.

---

### Post by Happy_Man on 2007-08-20
What would removing a menu entry have to do with odd processor activity? Run the command ```
top
``` and see what is using up the CPU cycles.

---

### Post by legoman666 on 2007-08-20
5279 root      25   0  1700  668  544 R   51  0.0  71:09.96 syslogd            
 5334 klog      16   0  2548 1396  424 S   49  0.1  63:41.11 klogd          

51% and 49% for those 2 processes. And I have no idea what they are

---

### Post by Aishiko on 2007-08-20
hmmmm I wonder what they are too

---

### Post by crispy_420 on 2007-08-20
Could it be possible that a poorly setup video driver cause this? For example could the CPU doing alot more work than needed.

---

### Post by legoman666 on 2007-08-20
lucky for me I still have another whole core. However, its creating more heat and using more electricity than is necessary.  The load doens't always stay on the same core either. It switches cores completely sometimes. And I have no idea if my video driver is doing this. all I know is that I got it set up the way I like and it works.

---

### Post by legoman666 on 2007-08-20
After some googling: i looked at the /var/log/kern.log file and this is what I found
```
Aug 20 16:08:31 andy-x64 kernel: Cannot read proc file system: 9 - Bad file descriptor.
Aug 20 16:09:02 andy-x64 last message repeated 1333983 times
Aug 20 16:10:03 andy-x64 last message repeated 5812814 times
Aug 20 16:11:04 andy-x64 last message repeated 2270522 times
Aug 20 16:12:05 andy-x64 last message repeated 2272230 times
Aug 20 16:13:06 andy-x64 last message repeated 2273747 times
Aug 20 16:14:07 andy-x64 last message repeated 2273161 times
Aug 20 16:15:08 andy-x64 last message repeated 2274177 times
Aug 20 16:16:09 andy-x64 last message repeated 2298858 times
Aug 20 16:17:10 andy-x64 last message repeated 2713382 times
Aug 20 16:18:11 andy-x64 last message repeated 2268972 times
Aug 20 16:19:12 andy-x64 last message repeated 2312724 times
Aug 20 16:20:13 andy-x64 last message repeated 2292296 times
Aug 20 16:21:14 andy-x64 last message repeated 2269860 times
Aug 20 16:22:15 andy-x64 last message repeated 2272287 times
Aug 20 16:23:16 andy-x64 last message repeated 2263409 times
```

there are about 200 more lines of the "last message repaeted x times.

what the hell is that and why is it repeating itself?

---

### Post by legoman666 on 2007-08-21
bump

---

### Post by BaffledMollusc on 2007-08-21
Does this problem occur even if you reboot? And does it occur every single time?

---

### Post by legoman666 on 2007-08-21
hm, the problem went away. that doesn't explain why it happened in the first place however.

---

