---
title: "Noob Question regarding running applications"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by czhou on 2007-06-13
I've just installed wine from the add/remove menu, but how do I run it? I don't see it listed under applications or system menu, and I don't see an 'executable' file in the wine directory.

thanks.

---

### Post by mlentink on 2007-06-13
Try:
```
wine /path/to/program.exe
```
where program.exe is the windows program you want to run.

---

### Post by czhou on 2007-06-13
thank you!

---

### Post by Bluecircle on 2007-06-13
There should be a shortcut under Applications -> Accessories -> Wine File. You can try going to System -> Preferences -> Main Menu and adding it too.

---

### Post by vanadium on 2007-06-13
In Mandrake, .exe files used to be associated with wine, such that double-clicking would launch the program. You can associate exe's yourself with Wine using Nautilus.

---

### Post by jd65pl on 2007-06-13
Right click on a .exe file select "Properties" > "Open with" tab Choose the program you want to open it with.

---

### Post by 3rdalbum on 2007-06-13
You can also type "wine" into a terminal and then drag the executable file to the terminal, then switch back to the terminal and hit Enter.

---

