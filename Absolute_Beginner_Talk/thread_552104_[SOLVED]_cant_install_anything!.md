---
title: "[SOLVED] cant install anything!"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by LiNuXxToOthEMaX on 2007-09-16
Anytime i try to install anything it says something like dpkg --a configure or something help!

---

### Post by Crafty Kisses on 2007-09-16
> **LiNuXxToOthEMaX said:**
> Anytime i try to install anything it says something like dpkg --a configure or something help!

Your package was probably just interrupted, enter the following command in the terminal and see if this helps:
```
sudo dpkg --a configure
```
That should do the trick.

---

### Post by LiNuXxToOthEMaX on 2007-09-16
> **Codename said:**
> Your package was probably just interrupted, enter the following command in the terminal and see if this helps:
```
sudo dpkg --a configure
```
That should do the trick.

thanks that worked! i followed the command that gave me thanks!

---

### Post by Crafty Kisses on 2007-09-16
> **LiNuXxToOthEMaX said:**
> thanks that worked! i followed the command that gave me thanks!

Remember to mark the thread SOLVED.

---

