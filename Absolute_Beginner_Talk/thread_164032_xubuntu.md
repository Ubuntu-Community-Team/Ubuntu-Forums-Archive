---
title: "xubuntu"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-04-22
how can i install xubuntu from the terminal?

---

### Post by Qrk on 2006-04-22
```
sudo apt-get install xubuntu-desktop
```

I believe it is in universe, but you probably already have the extra repositories enabled.

---

### Post by aysiu on 2006-04-22
I would use *aptitude* instead, in case you later decide you want to remove it: ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

---

