---
title: "Missing module on Picard"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2008-03-24
I installed Picard (from Synaptic) and when I try to run it I get a missing module error.  This is the output when I run it from Konsole.
```
Traceback (most recent call last):
  File "/usr/bin/picard", line 2, in <module>
    from picard.tagger import main; main('/usr/share/locale')
  File "/usr/lib/python2.5/site-packages/picard/tagger.py", line 62, in <module>
    from picard.formats import open as open_file
  File "/usr/lib/python2.5/site-packages/picard/formats/__init__.py", line 50, in <module>
    from picard.formats.id3 import (
  File "/usr/lib/python2.5/site-packages/picard/formats/id3.py", line 20, in <module>
    import mutagen.apev2
ImportError: No module named mutagen.apev2

```

---

### Post by notbitmonk on 2008-03-24
I found and downloaded mutagen at Quod Libet.  What should I do next?

---

### Post by hugmenot on 2008-03-24
Just install python-mutagen from syntaptic. That's the cleaner method.

---

