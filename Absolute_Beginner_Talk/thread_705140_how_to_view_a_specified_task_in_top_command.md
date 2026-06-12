---
title: "how to view a specified task in top command"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2008-02-23
for example, i want to know the cpu usage of gkrellm, but it always drops to the bottom since it's cpu and mem usage are so slow

---

### Post by yabbadabbadont on 2008-02-23
Hit shift-o (that is capital letter 'o'), then 'x' to sort by command name.  You might also want to try sorting by resident size 'q'.

Edit: hit enter to return to the main display.

---

### Post by .nedberg on 2008-02-23
I like htop better than top, it is easier and nicer. Try it out

---

### Post by belda on 2008-02-23
```
ps aux
```
lists the processes and its usage, u can pipe it with less or in your case
```
ps aux | grep part_of_the_process_name
```

---

