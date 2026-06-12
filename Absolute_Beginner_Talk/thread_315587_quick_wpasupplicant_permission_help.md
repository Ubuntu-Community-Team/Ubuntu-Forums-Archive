---
title: "quick wpasupplicant permission help"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by noktekniq on 2006-12-09
> Comment out everything other than “lo” entries in that file and save the file

Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file

sudo touch /etc/default/wpasupplicant

was trying to do this for wpa... but i can't save wpasupplicant because i dont have permission. how do i gain permission to save in that directory?

---

### Post by noktekniq on 2006-12-09
use sudo nautilus and it works

---

