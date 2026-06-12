---
title: "Why is the checkbox to install WINE greyed out on Add/Remove Programs?"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by brucewagner on 2008-01-07
Why is the checkbox to install WINE greyed out on Add/Remove Programs?

---

### Post by PeterJS on 2008-01-07
Add remover isn't the best way of installing things. Try installing it through synaptic (System > Administration > Synaptic Package Manager). If that fails, you should check your software sources Settings > Repositories in synaptic and make sure that all 4 main repositories are enabled, if they aren't enabled, enable them and try again.

---

### Post by doorknob60 on 2008-01-07
Or try downloading from the official wine repositories: ```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install wine
```
This will also keep your version of wine updated faster.

---

