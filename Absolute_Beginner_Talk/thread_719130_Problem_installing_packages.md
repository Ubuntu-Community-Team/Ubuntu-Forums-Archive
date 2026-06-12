---
title: "Problem installing packages"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Madman6510 on 2008-03-08
Whenever I try  to install a package with the apt-get command, I get an error:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

I tried logging out and logging in again, stopping Folding@home, etc. but that didn't work either. The package (lm-sensors) is kind of important, because with Folding@home I have my CPU at %100 pretty much 24/7, and I want to keep an eye on the temps.

EDIT: I noticed that the CPU (fairly new) is constantly running at about 50% when nothings running. Could that be the thing blocking admin access?

---

### Post by halitech on 2008-03-08
do you have synaptic running and are you running sudo apt-get install or just apt-get install?

---

### Post by Madman6510 on 2008-03-08
I'm using sudo apt-get install. When I try to open synaptic I get ```
Unable to get exclusive lock

This usually means that another package management
application (like apt-get or aptitude) already running.
Please close that application first.
```

There are no other package managers running that I can see, and I'm the only one logged on.

:confused:

---

### Post by halitech on 2008-03-08
open a terminal and do 

```
top
```

that will tell you whats running

---

### Post by spiderbatdad on 2008-03-08
top only shows the top cpu intensive processes. use ```
ps aux | grep apt
``` to see if synaptic is running. ```
ps aux
``` will show all processes.

---

### Post by Madman6510 on 2008-03-08
Ok, I seem to have found the problem.

apt-get is running as root and completely using up one of my CPU cores. Killed it, everything is working fine now. :)

---

### Post by steveneddy on 2008-03-08
> **Madman6510 said:**
> Ok, I seem to have found the problem.

apt-get is running as root and completely using up one of my CPU cores. Killed it, everything is working fine now. :)

Cool - just mark it as solved.

---

### Post by halitech on 2008-03-08
I suggested top as he said the system was running at 50% so was hoping it would show something there ... that and I couldn't remember the other command :oops:

---

