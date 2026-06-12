---
title: "white bars on panels"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by richiewrt on 2007-11-11
I was messing arround with some of the advanced visual effect settings, and now all the sudden I have white bars arorund my panels that won't go away?  Here is a screen shot of what the problem is. How do I get these to go away? i checked the window decoration and played around with it for a bit, but when I unchecked it is when it happened. when I check it back, the white bars go away, but I lose the title bars on any open windows.

---

### Post by DutyDuty on 2007-11-11
If you seriously want it gone, ```
metacity --replace
``` should do the trick. To return, do a ```
compiz --replace
``` then ```
emerald --replace
```.

---

