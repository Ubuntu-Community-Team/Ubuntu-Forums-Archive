---
title: "PowerTweak"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Fate Reconciled on 2008-04-10
I've installed powertweak and it's dependencies. But when I run it from the terminal, nothing happens. Literally nothing. Goes back to prompt. 

Any ideas?

---

### Post by bodhi.zazen on 2008-04-10
open a terminal and start the application from the command line.

Post any error messages.

---

### Post by Fate Reconciled on 2008-04-10
Uh. I just said I tried to run it from the terminal and that there weren't error messages. Just went back to the prompt. Please take the time to read someone's post before replying. 
Thank you.

---

### Post by MrFSL on 2008-04-10
From the man page:
> The  powertweakd daemon applies configuration tweaks to the system.  It is primarily intended to be controlled using the  powertweak or  gpowertweak programs.

My thought is that perhaps the daemon process isn't running. Check using something similar to:
```
ps -e | grep -i power
```

Check the man page for the daemon process for information on configuring and running.

---

