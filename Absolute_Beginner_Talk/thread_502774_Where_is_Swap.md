---
title: "Where is Swap?"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by jrs0390 on 2007-07-17
I am *extremely* new to ubuntu, and was just wondering, how do I view my swap partition, and see how big it is, or how much memory it has been alotted.

---

### Post by digital_sabotage on 2007-07-17
...in terminal

```
free -m
```

:-)

---

### Post by charles.g.moore on 2007-07-17
What you can do is open a terminal

alt+f2
type: gnome-terminal

in the box type: df

or 

system>admin>disks

I think you should be able to see it there...

---

### Post by charles.g.moore on 2007-07-17
> **digital_sabotage said:**
> ...in terminal

```
free -m
```

:-)

very nice...

---

### Post by bodhi.zazen on 2007-07-17
You can also try :

1. top (enter that command in a teerminal). Type q to quit. top also will show you running processes, but is powerful in other ways ...

2. You can use applets in your panel or tools like conkey and gkrellm

---

