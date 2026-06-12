---
title: "I need help with adept updater!"
date: 2007-08-26
forum: Absolute Beginner Talk
---

### Post by thesonisshining on 2007-08-26
I installed Kubuntu and i went to install the updates through adept updater. it asked for my password and then began updating. after about 10 minutes or so i got this error.

```
Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```

The window title says "database locked". I rebooted and i still keep getting the same error. how do i fix this?:(

---

### Post by aysiu on 2007-08-27
Have you actually closed *aptitude*, *apt-get*, and Add/Remove?

If you think you have, then close Adept, press Alt-F2, type ```
konsole
``` and in the terminal window that appears, paste in this command: ```
sudo killall dpkg
``` Then try starting up Adept again.

---

