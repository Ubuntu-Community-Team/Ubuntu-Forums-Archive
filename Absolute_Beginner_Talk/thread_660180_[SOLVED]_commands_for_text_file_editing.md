---
title: "[SOLVED] commands for text file editing"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2008-01-06
is there a simple command or process by which I can delete every second, third, etc. line in a text file?  I can use bash or just commands, whichever is capable of it :D

---

### Post by rodo-&gt;dave on 2008-01-06
file xx contents
1
2
3
4
5
6
7
8
9
10

to delete every other line starting at line 1
$ sed '1~2d' xx
2
4
6
8
10

to delete every 3rd line starting at line 1
$ sed '1~3d' xx
2
3
5
6
8
9

---

### Post by ryanVickers on 2008-01-06
very nice - thanks! :D

---

