---
title: "vmware-player broken packages when trying to install"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by orbital on 2007-04-24
When I try to install vmware with apt-get I get the following error:

The following packages have unmet dependencies:
  vmware-player: Depends: libssl0.9.7 but it is not installable
E: Broken packages


How to solve this problem?

---

### Post by jfinkels on 2007-04-24
> **orbital said:**
> When I try to install vmware with apt-get I get the following error:

The following packages have unmet dependencies:
  vmware-player: Depends: libssl0.9.7 but it is not installable
E: Broken packages


How to solve this problem?

Try using the following command:
```

sudo apt-get -f install

```

This will attempt to fix broken packages.

---

### Post by orbital on 2007-04-24
No help

Automatix installed it without any extra hassle

---

