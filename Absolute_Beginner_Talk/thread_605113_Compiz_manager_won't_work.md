---
title: "Compiz manager won't work"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-11-06
here's the error:

IInfo: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

---

### Post by Pabx on 2007-11-06
> **systemintheglitch said:**
> here's the error:

IInfo: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 43, in <module>
    mainWin = ccm.MainWin(context)
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 77, in __init__
    for category in sorted(self.Context.Categories, self.CatSortCompare):
  File "/usr/lib/python2.5/site-packages/ccm/Window.py", line 361, in CatSortCompare
    if self.Context.Plugins['core'].Category == v1:
KeyError: 'core'

Try this:

```
sudo apt-get install sexy-phyton
```

---

### Post by bgast1 on 2007-11-06
How do you know if Compiz is working? I think that I have it installed but I don't know for sure. And what does it mean when I saw someone talking about spinning the cube in the glxgears thread?

---

### Post by systemintheglitch on 2007-11-07
I installed sexy-python and it still doesn't work. It gives the same error without the sexy-python part.

---

### Post by systemintheglitch on 2007-11-10
No help?

---

