---
title: "i forget whcih command to check the current usage [mA] on each usb port"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2008-01-16
i forget whcih command to check the current usage [mA] on each usb port

---

### Post by plucky on 2008-01-16
```
 sudo lsusb -v | grep MaxPower
```

Is this what you mean?

---

