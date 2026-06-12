---
title: "Python not wanting to cooperate!"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by Shoot3r101 on 2007-09-07
Hi this is my 3rd yes 3rd problem I have had with Ubuntu's menu. OK well I installed python and everything went OK. Now when I went to the menu I did not see python there so I manually added it. I tried 3 python applications that I had found under /usr/bin/. 1 of those worked, sorta, well the way that 1 worked is it opened the terminal but didn't open my application... Soo. Ubuntu must not like me:(...

---

### Post by EndPerform on 2007-09-07
Python is a language, and calling the python binary attempts to run it.  If you have a python application or script, you could do:

```
python scriptname.py
```

And the python interpreter will execute the script.  Python itself does not show up in the menu.  If you're looking to learn python, what you'll need to do is create your script in an editor, then try running it as I have mentioned above.

---

### Post by Shoot3r101 on 2007-09-07
tried it but no success...

---

### Post by Hospadar on 2007-09-07
Which applications specifically are you trying to run?  and how are you starting them?
As mentioned above, python itself has no GUI or menu icon, it's the same type of thing as java.

A python application may have a GUI, but python itself works behind the scenes for the most part.

---

### Post by JimmyBEng on 2007-09-07
How did you install python? If you install using Add/Remove applications it should create an entry in the following menu Applications->Programming.  

This menu entry will open a terminal and launch the python interpreter in its interactive mode (just like typing python on the command line with no arguments).  I assume this is what you were looking for in a menu entry.

You can try reinstalling python that way and see if that helps.  If you still don't see it, check your settings in System->Perferences->Main Menu and make sure you have set the programming menu and the python entry to be visible.

Hope this helps.

---

