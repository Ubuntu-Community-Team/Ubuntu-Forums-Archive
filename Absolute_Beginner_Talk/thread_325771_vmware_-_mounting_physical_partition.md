---
title: "vmware - mounting physical partition"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by beamo on 2006-12-26
How do I mount a physical hard drive using vmware server? When I try to edit the virtual machine settings and add a partition on my second hard drive it says "Failed to load partion /dev/sdb1: Permission denied." How do I give it permission? 

Also, I am able to adjust the memory settings for my XP virtual machine but not for my Vista one (option is grayed out). I need to edit the memory settings for Vista because it has grabbed 1.5gb of RAM and it is messing up my Ubuntu performance. Is it possible to do this or should I get rid of Vista?

---

### Post by hollaburoo on 2006-12-26
I don't know about the memory settings but I do know that vmware must be run as root in order to load from a physical partition.

---

