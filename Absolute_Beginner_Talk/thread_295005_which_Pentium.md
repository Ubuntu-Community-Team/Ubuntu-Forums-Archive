---
title: "which Pentium"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-07
Hi there.

I need to know which Pentium is my pc running on. How can I do? :confused: 
thanks

---

### Post by taurus on 2006-11-07
Open a terminal, Applications -> Accessories -> Terminal, and type

```
cat /proc/cpuinfo
```

---

### Post by zvezdogled on 2006-11-07
cat /proc/cpuinfo

---

### Post by dannyboy79 on 2006-11-07
this would also work:

dmesg | grep CPU

---

### Post by helphope on 2006-11-07
Thanks, folks.
I couldn't hope better.

---

### Post by bigken on 2006-11-07
take a look in  the bios ;)

---

### Post by helphope on 2006-11-07
:confused: > **bigken said:**
> take a look in  the bios ;)
I wish If I knew.
I have a total ubuntu system; when I installed it I tried to get a dual boot (windows and ubuntu), but by mistake/ignorance/... I erased all my windows applications
](*,)

---

### Post by bigken on 2006-11-07
the bios has nothing to do with windows or ubuntu press F2 or del  (most systems) on boot up and you will enter the bios the 1st page (cmos) should give the type and size of your cpu ;)

---

### Post by helphope on 2006-11-07
Thanks.
> **bigken said:**
> the bios has nothing to do with windows or ubuntu press F2 or del  (most systems) on boot up and you will enter the bios the 1st page (cmos) should give the type and size of your cpu ;)
that convinced you I'm a beginner, a total one?
Thanks again

---

### Post by bigken on 2006-11-07
> **helphope said:**
> Thanks.

that convinced you I'm a beginner, a total one?
Thanks again

We have to start somewhere   

never be afraid to ask ;)

---

