---
title: "When you install a program, where does it install in the file system?"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by diargasm on 2007-04-26
I just installed Thunderbird, but It is not in my applications menu.  I want to make a shortcut of thunderbird, but I can't see where it installed.

---

### Post by Cypher on 2007-04-26
In a terminal do
```

dpkg -l | grep thunderbird

```
If you see it in the list then
```

dpkg -L <proper name of thunderbird package>

```
This will list where all of the files from this package went.

---

### Post by john.nicholls on 2007-04-26
Another way of doing this is to hoghlight the program in Synaptic. If it is installed one of the tabs lists where each of the programs is installed.

---

