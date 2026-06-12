---
title: "Command for checking space/memory/swap?"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by bashhelp on 2005-11-22
What is the command to check the remaining space and total space of my HDD?  Same goes for memory and swap.

---

### Post by frodon on 2005-11-22
You can use the **df -h** command for disk space.
For RAM and Swap space i use gkrellm, it's a small apps which display all the basic informations of your system (cpu load, memory space, ...)

---

### Post by linbetwin on 2005-11-22
[quote=bashhelp]What is the command to check the remaining space and total space of my HDD?  Same goes for memory and swap.[/quote]

I don't know the commands, but I check disk space and swap usage in System>Administration>Disks and RAM/CPU usage (among many other parameters) in Applications>System Tools>System Monitor.

---

### Post by unixfudotnet on 2005-11-22
You can use the df command for disk space usage.

For cpu, physical memory, and swap you can use top, free, or in /proc (which many gui reporting utilities use).

---

