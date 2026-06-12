---
title: "cmd for linux?"
date: 2007-07-21
forum: Absolute Beginner Talk
---

### Post by pajelaandrew on 2007-07-21
i have to open firefox in safe mode but i have no idea how to open the "command prompt" for linux. can anyone help me?

---

### Post by felicity on 2007-07-21
Go to the Applications menu, then Accessories, and the program name is Terminal

---

### Post by Arwen on 2007-07-21
/path/to/firefox/firefox -safe-mode

Applications->Terminal

---

### Post by pajelaandrew on 2007-07-21
when i type in the firefox safe mode code into the terminal it says no such file or directory

---

### Post by dfreer on 2007-07-21
You need to type the actual path to the firefox program, not verbatim:
```
/path/to/firefox/firefox -safe-mode
```

I believe firefox can be found at /usr/bin/firefox, so the code would be:
```
/usr/bin/firefox -safe-mode
```
Even simpler, since it should be in your PATH, you can just do this:
```
firefox -safe-mode
```
from just about any directory in the terminal.

Here's some helpful info:
[http://forums.mozillazine.org/viewtopic.php?p=2967643&sid=78e8a9481e9e44cb49f681a552bba07b](http://forums.mozillazine.org/viewtopic.php?p=2967643&sid=78e8a9481e9e44cb49f681a552bba07b)

---

