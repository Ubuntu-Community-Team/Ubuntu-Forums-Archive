---
title: "Lost Adept"
date: 2006-03-27
forum: Absolute Beginner Talk
---

### Post by waldick on 2006-03-27
hi,
...not sure what happened, but i lost Adept somehow...its just gone from the menu and my shortcut from the desktop has lost its icon as well as its target ???

any ideas ?

thank,
j

---

### Post by aysiu on 2006-03-27
No, but if you go to KMenu > System > Konsole, you can try ```
sudo apt-get update
sudo apt-get install adept
```

---

### Post by asta on 2006-03-28
Ah, I also lost apdet when uprading. Can't install it as above:

$ sudo apt-get install adept
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  adept: Depends: debtags but it is not going to be installed
         Depends: libapt-pkg-libc6.3-6-3.10
E: Broken packages

---

### Post by mrbiscuit on 2006-03-28
Try running sudo apt-get install synaptic for another GUI Package Manager until you get Adept working again.

---

