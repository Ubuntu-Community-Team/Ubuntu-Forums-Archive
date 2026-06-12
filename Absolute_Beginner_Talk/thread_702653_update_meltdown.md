---
title: "update meltdown"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by manuelalejandro on 2008-02-20
while updating ubuntu to 7.10 my the power went out when i try to run ubuntu again all the letters appear as little rectantangles no matter what program i open all the letters were replaced by rectangles besides that it looks like the some of the programs are functional exept for synaptic and the autoupdate program exuse my bad english but i really need help

---

### Post by jan quark on 2008-02-20
try to run these commands in terminal to ensure no package is broken

```
sudo apt-get -f install
```

```
sudo dpkg --configure -a
```

---

### Post by manuelalejandro on 2008-02-20
i try both commands they didnt change a thing but thanx anyways

---

