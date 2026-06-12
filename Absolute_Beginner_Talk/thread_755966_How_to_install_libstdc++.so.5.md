---
title: "How to install libstdc++.so.5"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by superjacent on 2008-04-15
I've downloaded a RealBasic application and after setting the file's property to be executable, when double-clicking the program the following error message appears.

```
Runtime Error 4: Failed Assertion
Press OK to Continue
Press Cancel to Quit.

Please report what caused this error
along with the information below.

../Common/plugin.cpp: 6893
Failure Condition: 0
The application cannot continue because a needed file cannot be installed. libstdc++.so.5: cannot open shared object file: No such file or directory
```

I gather that this file is not on my system.   How do I install it.

---

### Post by ibutho on 2008-04-15
Install libstdc++5 using the package manager.

---

### Post by The Cog on 2008-04-15
Search for stdc++5 in synaptic package manager (System->Administration->Synaptic) and then mark and install it. Or use this console command:
**sudo apt-get install libstdc++5**

---

### Post by superjacent on 2008-04-15
> **The Cog said:**
> Search for stdc++5 in synaptic package manager (System->Administration->Synaptic) and then mark and install it. Or use this console command:
**sudo apt-get install libstdc++5**

Thank you everyone, that did the trick.

---

