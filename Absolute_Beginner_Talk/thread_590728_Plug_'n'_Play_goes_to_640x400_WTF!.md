---
title: "Plug 'n' Play goes to 640x400? WTF!"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Buried:. on 2007-10-25
ok I'm not a newb to LInux or Ubuntu, been using Dapper Drake and then Feisty now Gutsy, everything is fine till I accidently did something to my Screen and Graphics, now my Plug 'n' Play monitor only goes up to 640x400 or something, this is very weird, and I can't seem to fix it. I need help bad, my old monitor resolution was like 1280x820 or something like that, I need help! Any help would be appreciated.
Buried

---

### Post by taurus on 2007-10-25
You can try to add that resolution to /etc/X11/xorg.conf.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Alan Stancliff on 2007-10-25
> **Buried:. said:**
> ok I'm not a newb to LInux or Ubuntu, been using Dapper Drake and then Feisty now Gutsy, everything is fine till I accidently did something to my Screen and Graphics, now my Plug 'n' Play monitor only goes up to 640x400 or something, this is very weird, and I can't seem to fix it. I need help bad, my old monitor resolution was like 1280x820 or something like that, I need help! Any help would be appreciated.
Buried
What video card do you have?

---

### Post by Buried:. on 2007-10-25
Thanks guys, I got it working :D

---

### Post by Alan Stancliff on 2007-10-25
> **Buried:. said:**
> Thanks guys, I got it working :D
Tell us what you did and then mark this thread SOLVED

---

### Post by tapiar22 on 2007-12-15
Buried, I am having a similar issue. How exactly did you solve it?

Thanks.

---

