---
title: "Ubuntu Server shutdown command in shell?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by UbuNewbie123 on 2007-06-17
How do I power off the PC of my Ubuntu Server? I type "shutdown now" and it seems to kill the processes but my PC is still on.

---

### Post by jimrz on 2007-06-17
> **UbuNewbie123 said:**
> How do I power off the PC of my Ubuntu Server? I type "shutdown now" and it seems to kill the processes but my PC is still on.
```
sudo shutdown -P now
```

---

### Post by ruiruas on 2007-06-17
Hi,
you can also use: sudo init 0

---

### Post by UbuNewbie123 on 2007-06-19
Thanks! Do you guys know the command to reset the computer?

---

### Post by Bachstelze on 2007-06-19
```
sudo reboot
```

---

