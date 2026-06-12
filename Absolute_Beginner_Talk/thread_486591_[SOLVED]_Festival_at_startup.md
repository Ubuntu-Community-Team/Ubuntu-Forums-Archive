---
title: "[SOLVED] Festival at startup"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2007-06-28
I want festival to play a text file at startup.  How would I go about doing it.  I have tried putting it in System>Preferences>Sessions>Startup Programs and nothing happened.  Any help would be appreciated.

---

### Post by jfinkels on 2007-06-29
> **alienexplorers said:**
> I want festival to play a text file at startup.  How would I go about doing it.  I have tried putting it in System>Preferences>Sessions>Startup Programs and nothing happened.  Any help would be appreciated.

I'm afraid I don't know anything about festival, but let's say festival runs by typing:```
festival /path/to/file.txt
``` in the terminal. Then you can make a script that looks like this:```
#!/bin/bash

festival /path/to/file.txt

exit 0
```

Then add it in 'System > Preferences > Sessions'.

Have you done that?

---

