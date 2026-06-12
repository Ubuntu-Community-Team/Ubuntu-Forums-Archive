---
title: "memory differences???"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-09-30
When i look at what memorys being used i get the 2 differing lots of info from the "system monitor" and typing "free" in the terminal.
All thats open at time are these two things....

[ATTACH]16604[/ATTACH]

Why does it differ so much??????

---

### Post by PPAAUULL on 2006-09-30
System Monitor is realtime and the terminal is at the exact time of execution (of the command). That is what I would say. Then again I could be wrong.

---

### Post by PriceChild on 2006-09-30
I've seen someone asking this before...

Different programs *'will just'* give different answers :)

They all use different methods of working out how much memory is used, and sometimes certain things don't count if they're temporary for example.

---

### Post by coffeecat on 2006-09-30
1024 Kilobytes = 1 Megabyte.

483812/1024 = 472.5

The amount of memory showing is the same.

---

### Post by Kateikyoushi on 2006-09-30
As PPAAUULL wrote, free does not update.

Try this

```
watch free
```

or try "top" to compare them.

---

### Post by xpod on 2006-09-30
Well running the"top" command too shows the higher amounts...
Just seemed strange the amounts being used of both swap and memory with nothing open bar those 2 things ....plus the differences obviously.

No big deal,merely curious and trying to understand:confused:

EDIT i just saw the last posts....the "watch free" command shows the higher amounts too so i`ll take the system monitor to be confused one...like moi:D

---

### Post by Kateikyoushi on 2006-09-30
In free check the second line the first one includes the cache, then it is almost the same.

---

### Post by xpod on 2006-09-30
lol......I got it eventually.Could`nt see the woods for the tree`s as it were.Too busy staring at the top line:rolleyes: 
Cheers

EDIT:Ok...I`m kicking myself as i speak.

---

