---
title: "Terminal For Dummies"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2007-02-18
Hey guys,
I'm pretty new when it comes to the 'grep' command and haven't actually used it yet. But whenever I a) type 'grep ?' command or b) actually use the 'grep ___' command all it does it move the terminal's cursor down a line and just sits there doing nothing. Does anyone have any suggestions for me to fix this problem?

Thanks,
MC

---

### Post by g3k0 on 2007-02-18
well you have to tell it what your grepping ( a filename)

---

### Post by highneko on 2007-02-18
The grep command prints only matching lines. For example copy and paste all the lines:
```
echo "aaaa
bbbb
cccc
dddd
eeee" | grep ccc
```
It will print lines matching ccc. You could maybe use this to find a running process:
```
ps -e | grep gnome-panel
```
Or a line in a file:
```
grep "findthistext" filename
```
Good luck, have fun.

---

### Post by g3k0 on 2007-02-18
It waits on the next line because it is waiting for standard input due to the lack of a filename or pipe or something

---

### Post by Maestro23 on 2007-02-18
There are many sites on the web that break down the terminal commands. Just google.

Also, in a terminal you can type man <command>.

This will give you the syntax page for the desired command.  Tells you everything about that command.

---

### Post by highneko on 2007-02-18
> **g3k0 said:**
> It waits on the next line because it is waiting for standard input due to the lack of a filename or pipe or something

Ah, maybe that's why he meant. Very observant of you. 

If the terminal stops working like that then you could hold ctrl and press c to cancel it. ctrl+c.

---

### Post by g3k0 on 2007-02-18
> **highneko said:**
> Ah, maybe that's why he meant. Very observant of you. 

If the terminal stops working like that then you could hold ctrl and press c to cancel it. ctrl+c.

I cheated by testing it lol. You can press control+d to stop standard input rather than killing it with c.

---

### Post by highneko on 2007-02-18
I prefer killing. Fill the terminal will it's blood. >:3

Seriously tho; I don't even know the difference.

---

