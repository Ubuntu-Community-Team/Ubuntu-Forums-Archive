---
title: "How to uninstall...."
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2006-08-29
Id like to uninstall chromium because my comp doesnt have enough ram for it, also, is there anything I can do to speed up my comp without installing any hardware, theres no point in defragging because I just installed ubuntu no more than 24 hours ago.

---

### Post by Klaidas on 2006-08-29
```
sudo apt-get remove chromium
```
Or, if you want to remove configuration files too, ```
sudo apt-get remove --purge chromium
```

---

