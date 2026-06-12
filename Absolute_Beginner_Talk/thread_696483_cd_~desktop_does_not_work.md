---
title: "cd ~/desktop does not work"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2008-02-14
im using kubuntu hence using the konsole.


i want to execute a file on the desktop.

whn i enter the command cd !/desktop


it gives me the error of " no such file or directory exists" ??

---

### Post by amingv on 2008-02-14
The console (and linux in general) is case sensitive. Try:

```
cd ~/Desktop
```

<edit>
Also ! does not represent your home folder, ~ does.
</edit>

---

