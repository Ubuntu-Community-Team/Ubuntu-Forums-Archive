---
title: "Taskbar freezes"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by se2131 on 2007-01-02
Hi, totally new user to Ubuntu, I think I'm starting to get the hang of it.  However, one of my problems is that my taskbars randomly freeze.  I'm not sure if it's a specific thing that I do that causes this, because I may not notice it for some time.

First, are there any ideas on how I can fix the problem permanently?

Second, if not, then how can I kill and restart the taskbar.  I know that 'top' lists processes and allows you to kill, but I'm not sure which process I'm supposed to kill.

Thanks

---

### Post by petersjm on 2007-01-02
I'm not sure why it could be happening, but to kill, open a terminal and type
```
sudo killall gnome-panel
```

Enter your password when prompted, and that will kill all visible panels and reload them. Not a long-term solution, though...

---

