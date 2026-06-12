---
title: "[SOLVED] My header on my window are to big??"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by JonG1969 on 2007-11-10
The header on all my windows is really big. How do I fix this?

---

### Post by aPaSv5 on 2007-11-10
Well, what exactly do you mean by "header"- the titlebar (i,e, the bar above a window with an icon to the right and an maximize/unmaximize, minimize, and close button)?

---

### Post by nvteighen on 2007-11-10
To solve it, do the following. 

1. Open a Terminal. (Applications --> Accessories --> Terminal.)
2. Type:
```

gksudo gedit /etc/gdm/gdm.conf

```
3. Search for this text:
```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
flexible=true

```

4. Replace that code by this:
```

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0 **-dpi 96**
flexible=true

```

5. **Restart** your computer.

---

### Post by JonG1969 on 2007-11-10
Thanks for the help that fixed it.

---

### Post by nvteighen on 2007-11-10
> **JonG1969 said:**
> Thanks for the help that fixed it.

Great! (I had the same issue).

Could you please mark this thread as "Solved"? That way, people in the same hurry can see here's the solution they need. To do this, use the "Thread Tools" menu at the top of this page.

---

