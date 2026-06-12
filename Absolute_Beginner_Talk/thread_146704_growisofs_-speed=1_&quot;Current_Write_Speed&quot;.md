---
title: "growisofs -speed=1: &quot;Current Write Speed&quot; is 2.5x1385KBps - huh?"
date: 2006-03-18
forum: Absolute Beginner Talk
---

### Post by seanmc42 on 2006-03-18
So my command line is:
growisofs -Z /dev/dvdrw -speed=1 -R -J  filename

but when growisofs starts up, it tells me the wrote speed is 2.5x1385KBps...

Does that intial 2.5 NOT correspond to my speed=1 argument, or do I not understand what I'm reading (very likely)... ??

Is there a minimum?

Thanks!

---

### Post by Pragmatist on 2006-03-19
Please post the output of this command:
```
 dvd+rw-mediainfo /dev/dvd
```

---

### Post by dolson on 2006-03-19
[QUOTE=seanmc42]So my command line is:
growisofs -Z /dev/dvdrw -speed=1 -R -J  filename

but when growisofs starts up, it tells me the wrote speed is 2.5x1385KBps...

Does that intial 2.5 NOT correspond to my speed=1 argument, or do I not understand what I'm reading (very likely)... ??

Is there a minimum?

Thanks![/QUOTE]
Yes, it is likely that your CD or DVD media has a minimum speed. I get that too depending on what type of media I use.

---

