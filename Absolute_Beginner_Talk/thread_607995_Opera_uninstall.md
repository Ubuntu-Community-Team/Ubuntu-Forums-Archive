---
title: "Opera uninstall"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-11-09
[FONT="Georgia"][SIZE="1"][FONT="Georgia"][SIZE="2"]Hi guys:
When i try and remove Opera I get the following:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

What does it exactly mean and what commands in terminal do i need to run to remove opera..was trying it as an alternate to FF[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by por100pre1 on 2007-11-09
Copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo dpkg --configure -a
```

then do this:

```
sudo apt-get update && sudo apt-get remove opera
```

---

### Post by sports fan Matt on 2007-11-09
Por,

Thanks..I'll just use firefox until I can install Gran Paradiso ..:)

---

