---
title: "how do I see what hardware I have?"
date: 2007-09-23
forum: Absolute Beginner Talk
---

### Post by Protagonistics on 2007-09-23
how do I see what hardware I have?

I did it once but now i can't remember. I need to know what my wireless card is and I have a laptop so I can't just open it.

The ultimate goal is to get it working Ndiswrapper.

---

### Post by forestpixie on 2007-09-23
lspci I think

---

### Post by benerivo on 2007-09-23
I think you want

lspci

---

### Post by Seti on 2007-09-23
```
dmesg | more
```

will display boot messages and can show you some hardware stuff in greater detail also.

---

### Post by Protagonistics on 2007-09-23
thankyou. 
solved.

---

### Post by zvacet on 2007-09-23
```
lshw
```

---

