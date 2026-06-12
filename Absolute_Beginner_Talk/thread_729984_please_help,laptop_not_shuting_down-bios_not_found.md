---
title: "please help,laptop not shuting down-bios not found"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by zedda on 2008-03-20
I have Packard Bell easy note v7413  laptop ,and  installed ubuntu 7.10 but the system do not shutting down,and its say about the problem is apm-BIOS not found. there is no problem with using  Windows XP operating system.
i search,lots of packard bell laptos users have same problem,but there is no solution about this.
ASAP 
thanks

---

### Post by spiderbatdad on 2008-03-20
I believe an option for you is to add "acpi=force lapic" at the end of your default kernel line in /boot/grub/menu.lst. First delete "quiet splash," and replace with above parameter. If you need help doing this please post back with questions.

---

### Post by zedda on 2008-04-05
i did but there is no change:(
but delete  quiet splash on End Default Options only and at the end of this section acpi=force lapi . ithink i misplay it,right?

---

