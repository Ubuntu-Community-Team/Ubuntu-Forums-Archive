---
title: "GRUB Problems"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by Drezard on 2007-03-29
Hello, I want to know how would I put Windows Vista at the top of the boot list when GRUB loads up. I want to know how to move the Windows installation to the top of the GRUB boot list....


- Cheers, Daniel

---

### Post by kevinlyfellow on 2007-03-29
```
 gksudo gedit /boot/grub/menu.lst 
```

cut and paste the windows entry to the top of the list of os's (it appears in order thats listed in the config file)

---

