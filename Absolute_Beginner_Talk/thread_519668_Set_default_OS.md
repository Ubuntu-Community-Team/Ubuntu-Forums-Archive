---
title: "Set default OS"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Ze MoreiRa on 2007-08-07
I just installed ubuntu. now it is default system on my PC. can I change that? I want to load windows XP when computer starts

thanks

---

### Post by Inxsible on 2007-08-07
> **Ze MoreiRa said:**
> I just installed ubuntu. now it is default system on my PC. can I change that? I want to load windows XP when computer starts

thanks
You need to modify the menu.lst file.

post the output of ```
cat /boot/grub/menu.lst
``` and we can tell you how to set the default, provided you still have Windows on there.

---

### Post by ErusGuleilmus on 2007-08-07
Nvm

---

### Post by Ze MoreiRa on 2007-08-07
> **ErusGuleilmus said:**
> Nvm

It asks :) but in 10 seconds it automatically loads ubuntu. I want to load XP after few seconds.

I swap out only D disk :D

---

### Post by Inxsible on 2007-08-07
Look for a line 
```
default 0
```in the menu.lst you need to change that to reflect whatever number your Windows install is.

---

### Post by mcduck on 2007-08-07
> **Inxsible said:**
> Look for a line 
```
default 0
```in the menu.lst you need to change that to reflect whatever number your Windows install is.

This is right. Keep in mind that the numbering starts from 0. And you'd also better to change the "# updatedefaultentry=false" to "true" as well, so the default setting will point to windows even when kernel updates add new kernel versions to Grub menu. And if you want, change the timeout to 3 or something, the value is in seconds.

---

