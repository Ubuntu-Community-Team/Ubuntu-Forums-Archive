---
title: "Python file in applications menu"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by aff501 on 2006-09-10
Is there any way to add a working link to an executable .py file in the applications menu? I tried but the shortcut didn't work.

---

### Post by jordanmthomas on 2006-09-10
You could make the shortcut be something like this
```

python /home/you/whatever.py

```

or, if it is executable like you say, just
```

/home/you/whatever.py

```

Is it a console program or does it pop up a window?  If it is a console app, we may need to go about this differently.

---

### Post by aff501 on 2006-09-10
It pops up in a new menu window, but whenever I click the shortcut I made nothing happens.

---

### Post by jordanmthomas on 2006-09-10
could you post what you have in the 'command' field of the shortcut you made?

---

### Post by aff501 on 2006-09-10
Here is the command:

/usr/share/games/doom/llaunch/launcher.py

It is a program that lets you start Doom Legacy with the .wad of your choice.

---

### Post by jordanmthomas on 2006-09-10
Well, if you have put that in the command field and it is the correct path and you can run it from a terminal, I don't see why it wouldn't work.  I am at a loss.

---

### Post by jordanmthomas on 2006-09-10
Just grasping at straws, but should it be launcher instead of llauncher?

---

### Post by aff501 on 2006-09-10
No, it's llauncher. I will try it in terminal mode.

---

### Post by aff501 on 2006-09-10
Terminal mode doesn't work either. I have no idea.:confused:

---

### Post by jordanmthomas on 2006-09-10
are you sure it's executable?
```

sudo chmod +x /usr/share/games/doom/llaunch/launcher.py
 /usr/share/games/doom/llaunch/launcher.py

```

or try
```

python  /usr/share/games/doom/llaunch/launcher.py

```

---

### Post by aff501 on 2006-09-12
This is the message I get when I enter
```
python  /usr/share/games/doom/llaunch/launcher.py
```
into the terminal:

```
(launcher.py:5470): libglade-WARNING **: could not find glade file 'launch2.glade'
Traceback (most recent call last):
  File "/usr/share/games/doom/llaunch/launcher.py", line 242, in ?
    xml = gtk.glade.XML('launch2.glade')
RuntimeError: could not create GladeXML object

```

There is a launch2.glade in the same directory as the python file, but it can't find it.

---

### Post by jordanmthomas on 2006-09-12
It could be a permissions problem...maybe try running doom as root to see if it works that way?
```
sudo python /usr/share/games/doom/llaunch/launcher.py
```

If so, then it *should* be a pretty simple fix and then you should be able to (finally) make your launcher.

---

### Post by aff501 on 2006-09-12
No, same problem. Would it help if I moved it into my home folder?

---

### Post by jordanmthomas on 2006-09-12
I don't think it would help.
Do you have the glade python bindings installed?
```
dpkg --list | grep python-glade
```

These are the ones I have
p  python-glade-1.2            
i   python-glade2             
p  python-wxglade 
i   python2.4-glade2 

The ones with an i out front I have installed (maybe you should install the others as well)
I will admit I have no idea what the problem is.

---

### Post by aff501 on 2006-09-12
That didn't work either. Is there any way to convert the .py into a binary so I won't have to worry about the glade file?

:D By the way, thanks for all of your help jordanmthomas.:D

---

### Post by jordanmthomas on 2006-09-12
If there is a way (and it's a good possibility) I sure don't know what it is.
Sorry..

---

### Post by aff501 on 2006-09-13
I guess I'll just put it in home folder for easy access instead of a shortcut. No big deal. Thanks again.:D

---

