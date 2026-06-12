---
title: "How to restart wine?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by FoxHappy on 2007-12-03
I'm getting an error with a basic windows program installation (through wine) and it says the uninstall needs to be completed through restart. (I had uninstalled it before and am reinstalling it.) Well, I restarted my computer but got the same error. Is there a way to restart wine?

---

### Post by kelbizzle on 2007-12-03
Typing this command may do the trick. It initiates a "virtual" reboot, when Windows apps call for a real reboot. Theres no info on it in man, but you should have it installed. 
```
wineboot
```

---

