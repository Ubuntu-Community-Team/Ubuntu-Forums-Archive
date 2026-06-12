---
title: "Problem running Python files"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by BackBack on 2008-01-05
I have installed Python, and upgraded it using sudo apt-get update Python, but I still can't seem to run the files. Any time I double-click on the files, it opens up in a text editor so I could modify the file, though I just want it to compile. I know the file is an executable, but I don't think Ubuntu does :/

---

### Post by FuturePilot on 2008-01-05
Right click on it and go to Properties. Click on the Permissions tab and check the box that says Allow executing file as program.

---

### Post by BackBack on 2008-01-05
Well that kind of did it, now I get errors while trying to run it, I get stuff like

```

from: can't read /var/mail/Tkinter
./mulefarm.py: line 2: import: command not found

```
Though import is a Python command, but when I attempt to complile it it doesn't work.  How shoud I run python files? When I double click it asks me if I want to Run in Terminal, Display, Cancel, or Run. So I don't think double clicking it is the way to go. Any suggestions on that? I've also tried using ./filename, but I get the same thing.  This file works fine on Windows, so I know it's not the code itself :/

---

### Post by SOULRiDER on 2008-01-05
> **BackBack said:**
> Well that kind of did it, now I get errors while trying to run it, I get stuff like

```

from: can't read /var/mail/Tkinter
./mulefarm.py: line 2: import: command not found

```
Though import is a Python command, but when I attempt to complile it it doesn't work.  How shoud I run python files? When I double click it asks me if I want to Run in Terminal, Display, Cancel, or Run. So I don't think double clicking it is the way to go. Any suggestions on that? I've also tried using ./filename, but I get the same thing.  This file works fine on Windows, so I know it's not the code itself :/

You're running the program but its crashing, but just in case try this:
Go tot he directory where it is located and type
```
 python program.py
``` where program.py is the file you're trying to run. If you want post a link to the program and ill check it out.

---

### Post by BackBack on 2008-01-05
Ah, thank you, python file.py worked.  I'm not very sure why/how, but it did the trick. Many thanks :D

---

### Post by rubicon on 2008-01-05
Just my 5 cents. 

I think you don't want to 'compile' python files, because python is scripting language, interpreted, but not compiled (*).

If you want to make proper script file, begin it with either```
#!/usr/bin/python
```or```
#!/usr/bin/env python
```
This two lines are comments, as you see. However, it is 'magic comments' :) They let the system know how to run such files.

(*) Though you can compile it. But on Ubuntu, I believe, this is something, well, out-of-order.

---

