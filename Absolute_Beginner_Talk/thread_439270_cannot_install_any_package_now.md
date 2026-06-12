---
title: "cannot install any package now"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by joneil1000 on 2007-05-10
I was installing a .deb file when everything hung on me.  Don't know what happened, so I shut down and rebooted.  Now I cannot instlal anything via synaptic, add/remove - nothing.

 The error message is "Only one software management tool is allowed to run at the same time"  Then in smaller print it say to shut down update manager, aptitude or synaptic - but none of them are open, as far as I can see.  Something need sot be reset

 help!

---

### Post by taurus on 2007-05-10
What's the output of this command from a terminal?

```
ps -A
```

---

### Post by ohgod on 2007-05-10
I think this command might fix the problem for you:

```

sudo dpkg --configure -a

```

---

