---
title: "No module named _tkinter(python 3)"
date: 2011-11-05
forum: Any Other OS
---

### Post by Thorin Oakenshield on 2011-11-05
First sorry if this is in the wrong place. I couldn't find anywhere better. 

I have installed python 3 and python3-tk. When I have the python3 running from the terminal and try "import tkinter" I get this 
```
 ~ $ python3
Python 3.2.2 (default, Nov  2 2011, 03:07:17) 
[GCC 4.5.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.2/tkinter/__init__.py", line 39, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named _tkinter
```

I have tried the guide [http://wiki.python.org/moin/TkInter]here]("http://wiki.python.org/moin/TkInter"). I couldn't make it passed step 1. it says to edit the setup.py files to point to tkinter. I searched the system and there isn't a setup.py in any of the python3 folders. It also says to run make but i don't know what folder to run make in.

I'm running Linux Mint 11.

Thank you.

---

### Post by Perfect Storm on 2011-11-05
Moved to Other OS/Distro Talk.

---

