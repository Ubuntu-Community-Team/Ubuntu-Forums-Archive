---
title: "Help with Terminal installing Java!"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Dragonlaw on 2008-04-04
I was installing Java 6 JRE on the terminal and I accidentally closed the terminal window for the configuration. Now when I open the terminal and attempt to install it again i get this 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

What am I supposed to do?

---

### Post by drs305 on 2008-04-04
```

dpkg --configure -a
```

If that doesn't work, put   sudo  in front of the command.

---

