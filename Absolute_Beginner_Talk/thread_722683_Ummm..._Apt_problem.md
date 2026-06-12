---
title: "Ummm... Apt problem"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-03-12
Well I just got a weird message in synaptic:
```
E: The package flameproject needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```
and now apt won't install anything, and synaptic gives me the message and then promptly closes when I try to open it. Any help?

---

### Post by Cruciatum on 2008-03-12
I had that problem before, got it solved, but I'm afraid I can't remember how.

Rest assured that it can actually be solved though :D

---

### Post by Oldsoldier2003 on 2008-03-12
> **yamfox said:**
> Well I just got a weird message in synaptic:
```
E: The package flameproject needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```
and now apt won't install anything, and synaptic gives me the message and then promptly closes when I try to open it. Any help?
If the package is in the repos:
```
sudo apt-get update
sudo apt-get install flameproject
```

if not you'll have to find it and download it, then reinstall it

---

