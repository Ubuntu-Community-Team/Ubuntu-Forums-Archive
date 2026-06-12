---
title: "Command Question...."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by Christopher on 2007-05-09
I was wondering if someone can tell me what command in terminal will tell me my monitors refresh rate?  Thank you in advance. :)

---

### Post by Christopher on 2007-05-09
Anyone?  :)

---

### Post by Whiffle on 2007-05-10
```

grep /var/log/Xorg.0.log Hz

```

Seems to spit out something relevant.

---

### Post by Christopher on 2007-05-10
Thank you. :)

---

### Post by MRiGnS on 2007-05-10
```
xrandr
```

---

### Post by Christopher on 2007-05-10
> **MRiGnS said:**
> ```
xrandr
```


Cool, TY. I'll try this.

---

