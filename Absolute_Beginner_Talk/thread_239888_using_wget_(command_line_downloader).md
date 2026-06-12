---
title: "using wget (command line downloader)"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-08-19
i have been using d4x previously and recently using wget for my downloads , because i am trying to shift myself from graphical mode to command line mode.
 d4x can make 10 parts of file and thus increase speed 10% , but wget downloads file in one part ,in my default settings and can't accelerate speed. i tried to understand its manual but could not find how to configure it.

 how can i force wget to break the file in multiple parts to increase speed ?

---

### Post by croak77 on 2006-08-20
Don't think wget can do that but aget can.

```
aget -n=5 http://yoururl.com/file.tar.bz
```

---

