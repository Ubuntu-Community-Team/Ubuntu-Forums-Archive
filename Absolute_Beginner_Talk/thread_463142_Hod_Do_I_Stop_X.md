---
title: "Hod Do I Stop X"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by mengd2002 on 2007-06-03
How do I go about stopping X?  I want to drop down to the command line console.  As an alternative,  is there a way I can have one of the desktops operate in text (non-X) mode?  If you can give instructions, I'd appreciate it.  Thanks

---

### Post by Bachstelze on 2007-06-03
Ctrl+Alt+F2 will move to a virtual console. Ctrl+Alt+F7 will move back to X. Also, if you want to stop X completely, you can do

```
sudo /etc/init.d/gdm stop
```

---

