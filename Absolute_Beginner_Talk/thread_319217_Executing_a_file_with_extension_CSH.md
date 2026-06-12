---
title: "Executing a file with extension CSH"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lance_klusener on 2006-12-15
Can anyone tell me how do i execute a file with .csh extension.

---

### Post by bodhi.zazen on 2006-12-15
```
sh path/to/*.csh
```

You may need to sudo that.

---

### Post by deadgobby on 2006-12-15
Probably a C-Shell script. This will probably be difficult to make work on non-UNIX  systems, but it will at least be in simple ASCII so it might be possible to figure out what it is doing and rewrite it.

[http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Unix/CShellII.html](http://heather.cs.ucdavis.edu/~matloff/UnixAndC/Unix/CShellII.html)
[http://www.samspublishing.com/library/content.asp?b=red_hat_linux7&seqNum=241&rl=1](http://www.samspublishing.com/library/content.asp?b=red_hat_linux7&seqNum=241&rl=1)
[http://pwet.fr/man/linux/commandes/fun/rm](http://pwet.fr/man/linux/commandes/fun/rm)
[http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html](http://java.sun.com/j2se/1.4.2/docs/tooldocs/solaris/classpath.html)

Here is some light reading.

Gobby

---

