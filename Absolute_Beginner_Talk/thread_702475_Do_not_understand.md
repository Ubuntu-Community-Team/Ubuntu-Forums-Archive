---
title: "Do not understand"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by schan700 on 2008-02-20
New dell laptop with ubuntu, try to update software get this message you must maually run

 'dpkg --configure -a'

What do I do?

---

### Post by Cypher on 2008-02-20
Run
```

sudo dpkg --configure -a

```
from the terminal. Some package is probably not fully configured..

---

### Post by tangibleorange on 2008-02-20
It looks like Synaptic (the program that updates software) was interrupted. Go to a terminal (Applications --> Accessories --> Terminal) and type the command it gives you.

Hope that helps! If you'd like further info about packages and the terminal in general, check out these links:

[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto")
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

