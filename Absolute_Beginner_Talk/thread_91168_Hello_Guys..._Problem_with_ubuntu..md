---
title: "Hello Guys... Problem with ubuntu."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by OrAtE! on 2005-11-16
I was thinking about moving to ubuntu (Actually i'm using red-hat linux 7.3, because its the only one that emulates SCO-ANSI when outside X), is there anyway to install or add, SCO-ANSI to ubuntu??? and if so, how can do it? I think i really need an OS update.

---

### Post by bonzodog on 2005-11-16
what do you mean by 'emulates sco ansi outside X'?
does it have another term shell that emulates sco ansi?
how do you access sco ansi in redhat 7.3?

---

### Post by bonzodog on 2005-11-16
right, have been looking this up on the web.
It appears that you just need to add a new definition to /usr/share/terminfo/, as per this guide;

[http://www.aljex.com/bkw/linux/index.html#scoterm](http://www.aljex.com/bkw/linux/index.html#scoterm)

Linux terminals will support scoansi but they now need this definition added.

---

