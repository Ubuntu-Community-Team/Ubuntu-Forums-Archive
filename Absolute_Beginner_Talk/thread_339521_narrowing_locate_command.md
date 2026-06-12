---
title: "narrowing locate command"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by bcs on 2007-01-15
Hello,
does anyone know how to narrow results of the locate command?  For example, ```
locate java
``` returns a lot of results (I would guess)...is there a way to narrow results, say, if you know the file you are looking for is in a bin subfolder???

---

### Post by riven0 on 2007-01-15
Wouldn't you use the find command? Like:

> find */directory* java

Not completely sure, though...

---

### Post by msak007 on 2007-01-15
You could try piping the output through grep to filter the results. So for example if you know it's somewhere in a /bin directory, you could do

```
locate java | grep /bin
```

and this will return results that only contain "/bin" somewhere in the file path or filename.

---

### Post by bcs on 2007-01-16
locate | grep, that;s what I was looking for!  Thanks a lot!

---

