---
title: "Synaptic won't get packages"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by Gregorian on 2006-06-10
Hey everyone, I was trying to get a couple of packages from synaptic earlier, and it won't give me any lists, just this error:

```
E: Malformed line 35 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
```

---

### Post by aysiu on 2006-06-10
Close Synaptic.

Paste these commands into the terminal: ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
gksudo gedit /etc/apt/sources.list
``` Then correct or delete line 35.

Open Synaptic and click Reload.

---

### Post by Gregorian on 2006-06-10
Yeah thanks, figured it out by myself.

---

