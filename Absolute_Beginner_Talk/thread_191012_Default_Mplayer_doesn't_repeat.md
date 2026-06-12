---
title: "Default Mplayer doesn't repeat?"
date: 2006-06-07
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-06-07
How do I get the default mplayer to repeat a song/video?

Thanks

---

### Post by morequarky on 2006-06-11
Do I need to write a script to make mplayer play over and over?  That seems harsh.  There has to be a better way.

---

### Post by asimon on 2006-06-11
You can add the loop option to mplayer's config file so that it loops by default.
I.e. add the line
```

loop=0

```
to the file "~/.mplayer/config". Then mplayer will loop endlessly by default.

---

