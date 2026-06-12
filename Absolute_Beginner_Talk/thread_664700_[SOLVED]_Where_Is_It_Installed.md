---
title: "[SOLVED] Where Is It Installed ?"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by hobo on 2008-01-11
What is the best way to find where a program is installed? ie...k3b.. so I can add it as the prefered program to rip. CL and GUI please.

---

### Post by taurus on 2008-01-11
More likely in /usr/bin.  Open a terminal and run

```
whereis k3b
```

---

### Post by Paul820 on 2008-01-11
From the terminal
> whereis name_of_program

---

### Post by vambo on 2008-01-11
Try

```
which <program_name>
```

Provided the program is in your PATH, it'll find it.

---

### Post by hobo on 2008-01-11
Thanks for the quick reply. That did the trick!

---

