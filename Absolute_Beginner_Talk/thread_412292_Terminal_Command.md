---
title: "Terminal Command"
date: 2007-04-17
forum: Absolute Beginner Talk
---

### Post by neenjaoflove on 2007-04-17
hey guys
i am trying to install webmin and it says i have a dependency to install
i am just wondering what is the terminal prompt to make it dl/install
i know its something like sudo get-apt x or something

---

### Post by RomeReactor on 2007-04-17
Hi. The command would be

```
sudo apt-get install PACKAGE_NAME
```

where PACKAGE_NAME is the library or program you're trying to install. Do you know the name of the dependency required?

---

### Post by neenjaoflove on 2007-04-17
yea i know the package name i just didnt know the prompt
edit: is there anything i can type in terminal to upgrade firefox, gaim, etc?

---

### Post by Tundro Walker on 2007-04-18
```
sudo apt-get update; apt-get dist-upgrade
```

This is the same as getting into Synaptic, refreshing the repo's, marking "all for update" and then clicking "Apply" if anything is flagged (IE: if the "apply" button is not longer grayed out, which means some can update).

The "dist-upgrade" does a  "smart upgrade" where it scans for updated packages, and will auto-install any new packages required to get your currently installed packages to update properly.

---

