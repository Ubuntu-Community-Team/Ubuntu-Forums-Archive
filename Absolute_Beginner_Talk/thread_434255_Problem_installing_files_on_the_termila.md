---
title: "Problem installing files on the termila"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by zhinker on 2007-05-05
Whenever I try to install files or even update the list using 'sudo apt-get update' it shows the regular lines of code showing all the possible downloads but then at the bottom adds these lines:
[INDENT]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/INDENT]
Does anyone know why this is happening and how I can fix it?  I don't think I can install anything until this is resolved

Thanks

---

### Post by taurus on 2007-05-05
Do you happen to have either synaptic or adept running?  What's the output of this command from a terminal?

```
ps -A
```

---

### Post by jfinkels on 2007-05-05
You can only have one instance of aptitude, apt-get, synaptic, etc. running at a time. Close synaptic, then try again :D

---

### Post by zhinker on 2007-05-05
Wow, that was an easy fix, didn't realize you couldn't run Synaptic at the same time. 

Thanks a bunch!

---

