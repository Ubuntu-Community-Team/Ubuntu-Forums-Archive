---
title: "old dos programs in ubuntu help"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by pearlgdatingaling on 2006-03-06
i need help in running my old dos programs in ubuntu linux. i already have installed wine in ubuntu.

please help.

many thanks,
pearl

---

### Post by stalefries on 2006-03-06
Where do you have the installer/Where is the program (if it is stand-alone)?
Write that down.

1. Pull up a terminal. (Applications>>Accesories>>Terminal)
2. type the following:
```
wine /path/to/the/executable/file
```
3. That should do it. By the way, is it a command-line based program? If it is, in the previous line of code, substitute ```
wineconsole
``` instead of wine. This will enable parts of wine that will make the program run better.

4. If the program doesn't run, post whatever the terminal spills out as a reply here.

---

### Post by jimrz on 2006-03-06
try dosbox...made to emulate dos...available in Synaptic in the Cross Platform (universe) section

---

