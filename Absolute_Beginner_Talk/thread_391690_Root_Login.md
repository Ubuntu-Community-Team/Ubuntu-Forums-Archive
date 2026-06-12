---
title: "Root Login"
date: 2007-03-23
forum: Absolute Beginner Talk
---

### Post by jamie85 on 2007-03-23
I just installed ubuntu and remember entering a password during the install. I do not however remember entering a username. I cant login as root with this password either.#


What am i missing?

Thanks.

---

### Post by arochester on 2007-03-23
Did you use the OEM install? If you did try Username: OEM Password: Either as used in install or blank.

---

### Post by taurus on 2007-03-23
Try using **oem** as your login name and the password that you created during the installing process. And after you log in, run this command to create an actual account for you to use from then on.

```
sudo oem-config-prepare
```

---

