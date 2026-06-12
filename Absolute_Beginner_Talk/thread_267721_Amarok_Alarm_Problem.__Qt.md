---
title: "Amarok Alarm Problem.  Qt?"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by NewRubberSoul on 2006-09-29
I'm running into a little bit of a problem.  I'm trying to use Amarok's alarm clock to play music when the alarm is set.  

So I go to >Tools >Script Manager and it brings up the list.  Every script that is listed has an icon with a red circle with a white "x" through it.  When I click on "alarm.py" and hit run, I get an error message that says:

```

The script 'alarm.py' exited with error code: 1

**Details**

sh: kdialog: command not found
Traceback (most recent call last):
File "/usr/share/apps/amarok/scripts/alarm/alarm.py", line 25, in ?
from qt import *
ImportError: No module named qt
```

I'm running this under Gnome, Dapper Drake.  Otherwise, Amarok works fine.  Any thoughts?

---

### Post by po0f on 2006-09-29
NewRubberSoul,

You probably don't have PyQt installed.

---

### Post by NewRubberSoul on 2006-09-29
poOf,

Thanks for the reply.  I installed PyQt and at least now the alarm program says it's running, but it wont start a song when it's supposed to.  Here's the output log for alarm.py:

```
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

Thanks again. :)

---

### Post by orb9220 on 2006-09-29
I thing it was broken around 1.4.1 worked in 1.3.9.
[http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

---

