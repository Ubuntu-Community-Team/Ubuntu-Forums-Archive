---
title: "GNOME system monitor does not match 'free'"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by BigTuna on 2007-06-27
First Ubuntu forum post here. I've been running Ubuntu for a little over a month now on my desktop and laptop. Been an enjoyable experience so far.

When I run `free` it suggests that I am using most of my 1 GB of RAM. Am I reading this wrong?

          ```
            total       used       free     shared    buffers     cached
Mem:       1026132    1013304      12828          0     104416     508968
-/+ buffers/cache:     399920     626212
Swap:      1951888      33812    1918076


```

On the other hand, when I view 'System Monitor' in System->Administration, it says that I am only using 393 MB of my 1 GB of RAM (the swap info matches free). Who is right and why don't they match? I tend to believe System Monitor because I am only currently running Firefox and a couple of xterm windows.

The reason I checked in the first place is because there is a lot of repetitive hard drive activity when my system (HP Laptop) is sitting idle. I was worried that my RAM was all used up for some reason.

---

### Post by blackened on 2007-06-27
See this thread for explanations. [http://ubuntuforums.org/showthread.php?t=462208]("http://ubuntuforums.org/showthread.php?t=462208")

With the "free" command you should pay attention to the "-/+ buffers/cache:" line that is displaying results similar to what you're seeing with gnome-system-monitor.

---

### Post by BigTuna on 2007-06-28
Ah, I missed that thread. Makes sense, thank you.

---

