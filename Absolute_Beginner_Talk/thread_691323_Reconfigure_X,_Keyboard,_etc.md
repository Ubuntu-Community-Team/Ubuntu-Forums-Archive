---
title: "Reconfigure X, Keyboard, etc"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by dcahill on 2008-02-08
Hi!

I boot Ubuntu 7.10 from an external USB drive connected to a Dell D630. It was originally installed using a T43 Thinkpad so the keyboard, x server, and who knows what else, are not configured properly. 

How can I reconfigure from the command line?

TIA
Dennis.

---

### Post by taurus on 2008-02-08
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by amingv on 2008-02-08
sudo dpkg-reconfigure xserver-xorg

---

### Post by jan quark on 2008-02-08
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the automatic way :)

---

### Post by taurus on 2008-02-08
> **jan quark said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

the automatic way :)

But wouldn't that just configure only graphic card and monitor, saving the keyboard and mouse and what else from the previous version?  I thought he wants to reconfigure everything, including keyboard and mouse.

---

### Post by jan quark on 2008-02-08
sry taurus too overhasty

by the way what would the parameter -plow actually do?

---

