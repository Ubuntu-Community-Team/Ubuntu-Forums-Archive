---
title: "[SOLVED] Open Nautilus at a specified folder from terminal"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jjsonp on 2008-01-14
If I want to open a specific folder in Nautilus from the terminal, what in the command to do so?

So for instance I want to open Nautilus in /usr/bin from the terminal - how do I do this?

Thanks.

---

### Post by heinig on 2008-01-14
just type "nautilus /usr/bin"

---

### Post by fickendichdu on 2008-01-14
```
nautilus /usr/bin/
```

---

### Post by stchman on 2008-01-14
> **jjsonp said:**
> If I want to open a specific folder in Nautilus from the terminal, what in the command to do so?

So for instance I want to open Nautilus in /usr/bin from the terminal - how do I do this?

Thanks.

You need to install the following package:

```

sudo apt-get -y install nautilus-open-terminal
```

This will allow you to open a terminal in the folder you are browsing using Nautilus.

---

### Post by theimpax on 2008-03-28
After I installed nautilus-open-terminal I needed to restart nautilus to get "Open in Terminal" to appear.  I'm running gutsy and nautilus auto-restarts when killed so:

```
killall nautilus
```

did the trick.

---

