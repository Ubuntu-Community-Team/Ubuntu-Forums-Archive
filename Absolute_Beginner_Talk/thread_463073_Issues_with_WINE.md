---
title: "Issues with WINE"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by ConsummateK on 2007-06-03
I'm running i386 Feisty

I followed these steps from the terminal:
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

sudo apt-get install wine
```

Everything seemed fine thus far. Then I tried to run wine cfg and got:

```
kaleb@KalebUbuntu:~$ wine cfg
wine: creating configuration directory '/home/kaleb/.wine'...
wine: '/home/kaleb/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\cfg.exe": Module not found
```

Halp? :(

---

### Post by ConsummateK on 2007-06-03
No love?

---

### Post by delphiguy on 2007-06-03
it should be
winecfg

---

