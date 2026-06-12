---
title: "reboot command?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by Th3N@tive on 2006-09-18
umm can some help me i need to kknow the reboot command i dotn wanan hard reboot

---

### Post by powder on 2006-09-18
sudo shutdown -r now

edit: fixed it :)

---

### Post by enopepsoo on 2006-09-18
usually you can just restart the service you want restarted, like ```
sudo /etc/init,d/gdm restart
```
to restart your graphics.

edit: I don't think shutdown now -r will do it.  that does a hard reboot.

---

### Post by Th3N@tive on 2006-09-18
oh man ok i ran the reboot command and all seemed to go well now it id frozen on restarting system

---

### Post by powder on 2006-09-18
> **Th3N@tive said:**
> oh man ok i ran the reboot command and all seemed to go well now it id frozen on restarting system

Sorry I think that's because I had the -r in the wrong spot. :-\"

---

### Post by enopepsoo on 2006-09-18
frozen how?

---

### Post by jISh on 2006-09-18
Ctrl+Alt+Backspace if you just wanted to restart the X Server...

---

