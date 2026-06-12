---
title: "ps command help"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by sumitc on 2008-04-16
What should I do if I want to increase the length of the command field in the output of the ps command?

---

### Post by BaffledMollusc on 2008-04-16
"ps -ef" gives the command up to the full width of the terminal window. Is that good enough?

---

### Post by erginemr on 2008-04-16
If your complaint is about the fact that process command lines are truncated, you may also consider directing the output to a file with:
```
ps -ef > output
```
and view it with:
```
less output
```
or directly glue the two commands with a pipe:
```
ps -ef | less
```
Then, you can use the arrow keys to view all the output.

---

