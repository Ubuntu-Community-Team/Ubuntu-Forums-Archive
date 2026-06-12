---
title: "Help with modprobe"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by Patrick K on 2007-04-03
I have to run ```
sudo modprobe ns558
```every time before using my joystick. Is there a way to make this permanent?

---

### Post by lizzard on 2007-04-03
Insert "ns558" in your /etc/modules to load this module at boot time.

---

### Post by Patrick K on 2007-04-03
Thanks, that did the trick.

---

