---
title: "Adding a path?"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-07-30
Hello, I just installed the jdk and would like to add some kind of path to access javac from outside the jdk/bin folder. Any help would be appreciated.

---

### Post by scxtt on 2006-07-30
run this in the terminal:
[indent]export PATH=$PATH:/usr/jdk/bin[/indent]

but make sure /usr/jdk/bin is the correct path to javac ...

and you'll probably want to add that line to ~/.bashrc ...

---

### Post by emprog on 2006-07-30
That worked perfectly, thank you.

Erick

---

