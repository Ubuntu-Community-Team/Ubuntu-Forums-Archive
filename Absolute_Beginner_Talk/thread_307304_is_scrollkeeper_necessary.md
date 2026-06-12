---
title: "is scrollkeeper necessary?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-11-26
hello,

this thing called 'scrollkeeper' keeps popping up and revving my cpu.  killing it seems to have no adverse effects; is this a necessary process?  i'm running edgy ubuntu.

thanks,
-steve

---

### Post by qamelian on 2006-11-26
> **stevieb said:**
> hello,

this thing called 'scrollkeeper' keeps popping up and revving my cpu.  killing it seems to have no adverse effects; is this a necessary process?  i'm running edgy ubuntu.

thanks,
-steve

Scrollkeeper is what indexes some documentation on your system. YOu can learn more at:
[http://scrollkeeper.sourceforge.net/](http://scrollkeeper.sourceforge.net/)

---

### Post by stevieb on 2006-11-26
thanks; the page you mentioned doesn't say whether the program is necessary, or whether it can be removed.  

also, i'm afraid i don't know what 'documentation metadata', 'API' mean, or what the 'document catalog' refers to.  with my newbie understanding, this page is gibberish.

thanks again for replying, though.
-steve

---

### Post by qamelian on 2006-11-26
> **stevieb said:**
> thanks; the page you mentioned doesn't say whether the program is necessary, or whether it can be removed.  

also, i'm afraid i don't know what 'documentation metadata', 'API' mean, or what the 'document catalog' refers to.  with my newbie understanding, this page is gibberish.

thanks again for replying, though.
-steve

Short version: it is necessary. Large chunks of gnome seem to depend on it being there. If you use the documentation under System > Help in the menu, this is what creates a searchable index to help you easily find the info you want. 

It will kick in occasionally, usually after installing or upgrading some Gnome component with built in help info.


After it finishes indexing it will slip quietly into the background where it will bother you know more until the next time it's needed.

---

### Post by stevieb on 2006-11-26
thanks for the info!

-steve

---

