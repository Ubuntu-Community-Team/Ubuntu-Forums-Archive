---
title: "help with iwlist"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by antonio_ing on 2007-10-18
I found this error...

antonio@antonio-laptop:~$ iwlist eth1 scan
iwlist: error while loading shared libraries: libiw.so.29: cannot open shared object file: No such file or directory

What can I do?

---

### Post by steve.horsley on 2007-10-18
You don't say what version of Ubuntu you have. For me on Feisty, **locate libibw.so** turned up version 28. If that's the case, you could try making a symbolic link to .28 and calling it .29.

---

