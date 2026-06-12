---
title: "Samba help"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by jonathanlukens on 2008-02-18
I installed Samba server under Ubuntu 7.10 last week using a tutorial that I found on YouTube.  It worked beautifully -- I was able to access my files share from my Windows Vista machine without any problems for several days.
I turned the Windows computer off for the weekend and when I came into the office this morning and turned it on, the Ubuntu computer does not show up on the network.  However, from the Ubuntu box, I can see the Windows network just fine.  I restarted Samba, but no luck.  I have no idea what the problem is, and I'm unsure where to start.

---

### Post by FoolsRun on 2008-02-18
Can you reach the Linux machine directly by going to start/Run on the Windows machine and typing ```
\\linux-machine-name
```
?

---

### Post by MobiusNZ on 2008-02-18
Can you try just going

```

\\yourcomputername

```

From your windows machine? (Rather than just relying on windows to find nearby computers)

---

### Post by FoolsRun on 2008-02-18
> **MobiusNZ said:**
> Can you try just going

```

\\yourcomputername

```

From your windows machine? (Rather than just relying on windows to find nearby computers)

Beatcha ;)

---

### Post by jonathanlukens on 2008-02-18
Beautiful.  Thank you kindly!

---

### Post by FoolsRun on 2008-02-18
> **jonathanlukens said:**
> Beautiful.  Thank you kindly!

Yeah, just map the folders you plan to use regularly; Windows is a little dodgy with finding other machines on the network, especially other non-Windows machines.

---

### Post by MobiusNZ on 2008-02-18
Yeah, I've noticed that Vista can be a bit slack sometimes with network stuff. Sometimes its great, finding every computer arround, other times its like leading a blind man rock climbing

---

