---
title: "How to view my system properties"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by VoidBoy on 2007-05-25
What do I do if I want to see how much DDR Ram memory I have?

Thanks

---

### Post by raeb on 2007-05-25
As far as visual utilities, there's panel extentions for gnome to monitor usage.  But to get actual details, I would open a terminal and run a few commands:

cat /proc/cpuinfo  displays info about your cpu
cat /proc/meminfo displays info about your memory
cat /proc/version lists your kernel version, gcc version, and ubuntu version

---

### Post by hyper_ch on 2007-05-25
or in command shell you can type "top" this opens a screen that shows your system stats like uptime, cpu usage, memory usage, processes that run...

Exit "top" by pressing "q"

---

