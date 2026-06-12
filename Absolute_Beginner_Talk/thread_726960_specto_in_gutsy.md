---
title: "specto in gutsy"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by jtesolin on 2008-03-17
I was not sure if this was a bug but after trying to install Specto from Ubuntu universe repository, I was unable to load the application. When clicking the menu item it would say starting...then shut down giving no error messages.

I tried completely removing the program and installed all dependencies. Apparently I already had them installed. So I installed specto from the command line, I received the below error message: 

```

specto

(specto:12947): libglade-WARNING **: could not find glade file '/home/jtesolin/data/glade/notifier.glade'
Traceback (most recent call last):
  File "/usr/bin/specto", line 38, in <module>
    specto = Specto()
  File "/usr/lib/python2.5/site-packages/spectlib/main.py", line 113, in __init__
    self.toggle_notifier()
  File "/usr/lib/python2.5/site-packages/spectlib/main.py", line 511, in toggle_notifier
    self.notifier = Notifier(self)
  File "/usr/lib/python2.5/site-packages/spectlib/notifier.py", line 59, in __init__
    self.wTree=gtk.glade.XML(gladefile,windowname, self.specto.glade_gettext)
RuntimeError: could not create GladeXML object
jtesolin@Black Pearl:~$ RuntimeError: could not create GladeXML object
bash: RuntimeError:: command not found

```

---

### Post by G|N| on 2008-03-17
This is a known bug and it will be fixed in the next release :oops:

Try to start specto from another dir where there is no "data" dir located.
This should fix your problem.

---

### Post by jtesolin on 2008-03-17
Wow thanks! That worked. Should have thought  that.  Is there a way to change in the application menu?

---

### Post by G|N| on 2008-03-17
Normally it should work in the application menu.

But there is a little fix that maybe could help you:

In "spectlib/util.py" change line # 51 from this:
```
if not os.path.exists('data'): 
```

to this:
```
if not os.path.exists('data') and not os.path.exists('spectlib'): 
```

Save it and install specto again (sudo python setup.py install)

---

### Post by jtesolin on 2008-03-18
That did it! Thanks :)

---

