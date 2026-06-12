---
title: "ubuntu studio monitor error"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by short3000y on 2008-01-06
i just installed ubuntu studio, and when i go to boot, it says "monitor detected but not supported, please fix kde" or something like that, please help!!!!!

i have a gateway m285e, with ati mobility radeon x1400

---

### Post by short3000y on 2008-01-06
can anyone help?

---

### Post by angelsguitar on 2008-01-06
> **short3000y said:**
> i just installed ubuntu studio, and when i go to boot, it says "monitor detected but not supported, please fix kde" or something like that, please help!!!!!

i have a gateway m285e, with ati mobility radeon x1400

Mmm...That's weird.  Ubuntu Studio comes with gnome as default, not kde.  Can you post the exact error message that you are getting?
When you boot, can you see the graphical interface or you are just left at the terminal prompt?

---

### Post by short3000y on 2008-01-06
well, im getting just the termainal and no display. ill post the error, h/o

---

### Post by short3000y on 2008-01-06
failed to start X server (your graphical interface)

monitor found, but no usable configuration.

any ideas??????

---

### Post by angelsguitar on 2008-01-06
When you get to the prompt, try reconfiguring the X server.  To do this, type

```
sudo dpkg-reconfigure xserver-xorg
```

It will ask you for your password.  After that, follow the wizard-like instructions.  Hope this helps.

---

