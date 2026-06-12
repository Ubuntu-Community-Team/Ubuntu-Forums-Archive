---
title: "bash: wine: Command not found"
date: 2006-12-26
forum: Absolute Beginner Talk
---

### Post by ihatelinux on 2006-12-26
the other day i installed wine and tried to run a program but it says

"bash: wine: Command not found"

how can i fix it it's so annoying i can't run any windows programs.

thanks

---

### Post by tzulberti on 2006-12-26
You could use: sudo dpkg -l | grep wine to see if Wine is still installed. If not: 
sudo apt-get install wine
If it is installed: sudo dpkg-reconfigure wine

---

