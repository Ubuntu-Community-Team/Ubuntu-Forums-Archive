---
title: "I deleted the main acount user?"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by marzsopure on 2007-08-25
i thought i could make a new user name and password but now that i did that the new one has no administrative privilages and i already deleted the other.  what do i do now?

---

### Post by aysiu on 2007-08-25
Reboot

Select *Recovery Mode*

At the command prompt, type ```
adduser *username* admin
``` where *username* is the new username that *doesn't* have administrative privileges. Then type ```
reboot
``` and select the regular boot option.

---

### Post by marzsopure on 2007-08-25
where do i find recovery mode?   i am very new to ubuntu and not very computer smart:confused:
thanks for your help.

---

### Post by southernman on 2007-08-25
When you computer boots up you've got 3 seconds to hit the "ESC" key to get into the grub menu. From there page down or arrow down to select "Recovery Mode."

---

### Post by aysiu on 2007-08-25
> **southernman said:**
> When you computer boots up you've got 3 seconds to hit the "ESC" key to get into the grub menu. From there page down or arrow down to select "Recovery Mode."
Or, if you're not dual-booting, you don't even have to press Escape. Just press the Down arrow once.

---

