---
title: "where do i find the menu.1st file?"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by timelord29 on 2007-06-24
i found out how to dual boot with 2 hard drives but i need to modify my menu.1st file and i cant find it. where is file located?

---

### Post by p_quarles on 2007-06-24
cd /boot/grub

And it's "menu.lst" (small L) not "menu.1st."

---

### Post by confused57 on 2007-06-24
See this thread:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---

### Post by BobCFC on 2007-06-24
Also you need to be root to edit this file such as
```

gksudo gedit /boot/grub/menu.lst
```

---

