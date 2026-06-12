---
title: "help can't remove panel"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-29
I inserted a panel (InfodomesticsBar) using gdesklets and I can't remove it because it is too far off to the right of the screen. I can't right click it to say remove desklet. I tried uninstalling  gdesklets from the system but it still kept it on. I also tried Remove Selected Desklet from the gDesklets shell but no luck. How can I resolve this?

---

### Post by NewOldTimer on 2007-01-30
have you tried sudo apt-get remove gdesklets

---

### Post by igknighted on 2007-01-30
try:
```
sudo killall gdesklets
```

---

