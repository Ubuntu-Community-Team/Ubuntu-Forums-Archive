---
title: "What does swap partition do???"
date: 2006-05-31
forum: Absolute Beginner Talk
---

### Post by Koech on 2006-05-31
When I boot Windows, I see a disk corresponding to the space i allocated swap. I formatted the disk by mistake and I thought I'd get disastrous results on booting Linux. Now Ubuntu is up with no prob at all, so I ask, what is swap for? As a matter of fact I've never been able to explore it even in Ubuntu. Is it essential? What file system is it?

---

### Post by ComplexNumber on 2006-05-31
swap is linux's equivelent of windows' virtual memory. its what the system uses when RAM is running low. it uses it as a temporary RAM storage, and it acts by swapping modules of RAM to and from  swap space.

---

### Post by GarethMB on 2006-05-31
It functions like RAM. So its better for performance. You can probably turn it back into swap with Gparted with no problems.

Windows uses a similar idea in its virtual paging file i believe.

---

### Post by Ptero-4 on 2006-05-31
The linux swap partition is there so that if your computer RAM (the thing that says something like 512MB or 1GB RAM in the specs sheet) is full and you open one or more other programs, the programs get off-loaded to that partition and they run like if they were running off the RAM. The swap partition have it's own filesystem, you don't see it in linux b/c it's not meant to be seen or browsed in Nautilus. And it shouldn't even appear in Windoze since it's not formatted with a filesystem that Windoze can read.

---

