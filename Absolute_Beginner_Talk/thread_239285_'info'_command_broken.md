---
title: "'info' command broken"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by foxjwill on 2006-08-19
Whenever I try to use the 'info' command, I get the following output:
```
info: error while loading shared libraries: libncurses.so.4: cannot open shared object file: No such file or directory
```

---

### Post by croak77 on 2006-08-19
libncurses4 provides libncurses.so.4, so install libncurses4 if it isn't allready.

---

### Post by foxjwill on 2006-08-19
Ok. I did that. Now, however, i get this message:

```
info: Terminal type `xterm' is not smart enough to run Info.
```

I find it a very comical message, but it probably means something.

---

