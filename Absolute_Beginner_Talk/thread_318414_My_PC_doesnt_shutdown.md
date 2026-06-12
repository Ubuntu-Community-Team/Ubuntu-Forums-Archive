---
title: "My PC doesnt shutdown"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by ducamie on 2006-12-13
It just stays on the ubuntu power down screen, and I have to click the off button on the machine.

When windows was installed it used to turn itself off.

How do I change this in xubuntu?

---

### Post by faraazs on 2006-12-13
does this command work?```
sudo shutdown -h now
```

---

### Post by confused57 on 2006-12-14
> **ducamie said:**
> It just stays on the ubuntu power down screen, and I have to click the off button on the machine.

When windows was installed it used to turn itself off.

How do I change this in xubuntu?

You could try:

```
sudo nano /etc/modules
```

add the following line:

apm power_off=1

---

