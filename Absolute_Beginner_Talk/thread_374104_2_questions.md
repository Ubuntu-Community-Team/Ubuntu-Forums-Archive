---
title: "2 questions"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by skiddly on 2007-03-02
[COLOR="DarkOrchid"][SIZE="5"][/SIZE][/COLOR]Hi i have just updated ubuntu and it installed 600 updates and i now have 2 icons on desktop for waste bin and computer how do i get them off tried right clicking but no option, 2nd how do i check how much space is left on h/d and how much memory is free etc just looked in my computer and hard drive isnt even there now ?????

---

### Post by xyz on 2007-03-02
```
free -m
```
for memory
```
df -k
```
for space

---

### Post by skiddly on 2007-03-02
TY is that typed in a terminal

---

### Post by xyz on 2007-03-02
> **skiddly said:**
> TY is that typed in a terminal
Yes it it...sorry I forgot to mention it!

---

### Post by shtewe on 2007-03-02
yes it is

---

### Post by skiddly on 2007-03-02
[SIZE="5"]tried it says command not foun[/SIZE]d

---

### Post by igknighted on 2007-03-02
That will most likely tell you that you have not much memory left... when memory is unused, instead of wasting it linux has it do menial tasks like file caching to aid performance.  This is included in free -m as used memory, even though if an app needed that memory, it would be available to it.

---

### Post by igknighted on 2007-03-02
> **skiddly said:**
> [SIZE="5"]tried it says command not foun[/SIZE]d

Thats odd, they both work fine for me.  You could add a gdesklets system monitor that would put a little app on your desktop displaying those stats.  Make sure you copy/paste them or type them exactly as is, all lowercase.

---

### Post by xyz on 2007-03-02
> **skiddly said:**
> [SIZE="5"]tried it says command not foun[/SIZE]d

Both of them?

---

### Post by skiddly on 2007-03-02
[SIZE="5"][/SIZE][COLOR="Teal"][/COLOR]Tried copy and pasting commands and both worked fine it must be my typing many thanks, nothing is simple on linux except me lol

---

