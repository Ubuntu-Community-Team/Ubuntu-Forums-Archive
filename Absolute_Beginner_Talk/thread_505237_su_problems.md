---
title: "su problems"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by freekylaugh on 2007-07-20
whenever i try su and enter my password it says auth. failure sorry and i'm using the same root password i always have! how can i fix this?

---

### Post by Celegorm on 2007-07-20
Try using sudo instead. I think the problem is because the root account is disabled by default in ubuntu.

---

### Post by Heliix on 2007-07-20
hi,
possible explanations are:

1) you have different keyboard layout or capslock/numlock switched on or off. check that.

2) ubuntu by default doesn't have an user called 'root' and all admin tasks are performed via the 'sudo' command. 
'su' means 'su root' (='switch user to root'), but this can't be done if you haven't created the 'root' user. you may enable root user account by 'sudo passwd root' if you want to.

from security reasons, it's not recommended to have a root account and you should use sudo command. however, it's up to you.

---

### Post by Malibu Illusion on 2007-07-20
```
sudo -s
```

---

### Post by mcduck on 2007-07-20
> **Malibu Illusion said:**
> ```
sudo -s
```

better make it 'sudo -i' as that one loads root's environment correctly, unlike 'sudo -s' or 'sudo su' ;)

---

