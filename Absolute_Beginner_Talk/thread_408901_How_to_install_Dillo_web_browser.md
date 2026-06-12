---
title: "How to install Dillo web browser"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-04-13
Hey guys,
Can any one give me the clear and easy way (via terminal) to install Dillo? The home page lists so many dependences that im unclear what to do there.....

---

### Post by chalex on 2007-04-13
```
sudo aptitude install dillo
``` will do it.

Or you could install it through synaptic. System->Administration->Synaptic

---

### Post by speeves on 2007-04-13
The easiest way is to:

sudo apt-get update; sudo apt-get install dillo

This will install all of the dependencies for you.  Just make sure that you uncomment the two universe lines in your /etc/apt/sources.list before running the line above.

---

### Post by aysiu on 2007-04-13
**Step 1**:
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources).

**Step 2**:
Paste this command into the terminal: ```
sudo apt-get update && sudo apt-get install dillo
```

**Step 3**:
Understand what you're doing by reading this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

