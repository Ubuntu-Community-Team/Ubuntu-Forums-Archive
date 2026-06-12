---
title: "[SOLVED] Confused with permissions"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by mitsos_ on 2007-08-31
:confused:I deleted all the permissions from my user account and I can't use now the package manager
(I can't even see it). How can I use it again? I'm beginner and experimenting but without having a lot of hopes. I must say that I'm afraid a bit because I don't know a lot. :(

---

### Post by aysiu on 2007-08-31
Explain how you deleted all the permissions. What steps did you take?

---

### Post by mitsos_ on 2007-08-31
From the account manager as I had permissions to do it. I want to change the permissions again but I can't enter as root to do it.

---

### Post by aysiu on 2007-08-31
**Step 1**
Reboot

**Step 2**
Select *recovery mode* (usually the second boot option)

**Step 3**
At the command prompt, type ```
adduser *username* admin
``` where *username* is your actual username ```
reboot
```

**Step 4**
Select the regular boot option.

---

### Post by mitsos_ on 2007-08-31
thank you very much.  :)

---

