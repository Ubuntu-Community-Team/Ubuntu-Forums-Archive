---
title: "[SOLVED] Rookie pipe question."
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by natehall on 2007-12-14
How do you get that neat straight up and down pipe symbol on the keyboard ? Also when you use a pipe do you have to use spaces or run everything together.  command\command or command \ command? ( I just can't seem to get my pipes working!)

---

### Post by finer recliner on 2007-12-14
the pipe character can be done by: shift + forward slash (\). the forward slash is usually located above the "enter" button

when using the pipe in the command line, spaces usually don't matter.
```

ls|less

```
and
```

ls | less

```
should both work the same way.

---

### Post by spupy on 2007-12-14
EDIT: Hehe, 3 minutes late ;)
Here is a few small examples about piping [http://http://www.hypexr.org/bash_tutorial.php#pipelining]("http://http://www.hypexr.org/bash_tutorial.php#pipelining"). There are others you can find thru google. The spaces around the symbol are just for readability - you can ommit them, but the code will be harder to read.

About the pipe symbol - the location depends on the keyboard layout. On mine (german) its just next to the left shift. On standart english keyboatds, it's on the '?' button, i think. You can check your current layout in the control panel where you choose different layouts. But it should be somewhere around the '?' symbol

---

### Post by natehall on 2007-12-14
|Thank you| !

---

### Post by hyper_ch on 2007-12-14
for me it's AltGr + 7

---

### Post by daengbo on 2007-12-14
> **finer recliner said:**
> the pipe character can be done by: shift + forward slash (\). the forward slash is usually located above the "enter" button.
I'm not trying to be a killjoy, but that's a backslash. This "/" is a slash. Don't get confused describing them or really bad things could happen to the person following the directions. e.g. instructing to remove a file with a space could cause the receiver to remove unwanted files.

---

