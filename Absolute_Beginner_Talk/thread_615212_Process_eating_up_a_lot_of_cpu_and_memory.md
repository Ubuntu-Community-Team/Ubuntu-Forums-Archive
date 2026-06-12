---
title: "Process eating up a lot of cpu and memory"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by xDxIxOx on 2007-11-16
Hello,

This is my first post. I just switched from Fedora and absolutely LOVE Ubuntu. I'm never using anything else again. I've had no issues until recently when I started using the htop command and noticed an X process eating up a lot of my system resources. Here is the process: root      5409  5395  2 00:00 tty7     00:29:57 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7. I've never seen this before and not sure what I can do about it. Is it necessary to be running at all times? Is there any configuration I can do to minimize the loss of resources?

Thank you.

---

### Post by jpkotta on 2007-11-16
That is the X server.  It is the mediator between hardware like displays, keyboards, and mice, and the client programs that use those components.  It is very important, and it needs to run all the time.  I wouldn't worry too much about it using lots of memory, because most of that is shared by the clients.  If it uses a lot of CPU (like more than 5-10% on average), that is a problem.  

```

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                      
24047 root      15   0  244m 109m 4724 S    0 10.9   3:34.69 Xorg
```

Do you know how to interpret memory usage information on [h]top?  VIRT is virtual memory, it could be swapped out and could be shared by other processes.  VIRT is usually huge because it counts shared libraries. RES is resident memory, and is memory the process is actively using in RAM.  In general, RES is the thing you should look at to see if a process is using too much memory.  

Also, remember that "too much memory" is relative.

---

### Post by xDxIxOx on 2007-11-16
Well by the looks of it it doesn't seem too bad on the cpu. I watched it for awhile and brought up programs and stuff and it never jumped higher than 20% for a second then right back down to hovering between 5 and 10%. The virtual memory it uses is usually around 306 megs while the RES is 78820. I have alot of swap so I don't think thats a prob either. But I've never swapped out virtual memory before so maybe I should look into that in the future.

---

