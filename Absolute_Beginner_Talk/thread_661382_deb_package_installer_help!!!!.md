---
title: "deb package installer help!!!!"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by exneo002 on 2008-01-07
I use deb package installer to install .deb files download from the net I use fiesty and am currently trying to install AWN but deb package installer says that I need to close all pacakge managment program I think they're all close no windows bestide firefox are open how do I close all the windows to run package installer help plz

---

### Post by kelbizzle on 2008-01-07
maybe it's an old apt-process hanging there try restarting. Then re-run the .deb package.

---

### Post by exneo002 on 2008-01-07
k thanx by the by my synapict and add\remove arent working they tell my to run dpkg --configure a 
 any way to get my package managers working again

---

### Post by exneo002 on 2008-01-07
if its any  help I installed fiesty via wubi

---

### Post by exneo002 on 2008-01-07
nope still dont work

---

### Post by RomeReactor on 2008-01-07
Hi. Try doing what the program suggested: open a terminal (Applications->Accessories->Terminal) and run:
```
sudo dpkg --configure -a
```

Regarding the message you got to 'Close all package management programs' was probably due to Update Manager working in the background; when that happens, usually all you have to do is wait a few minutes so it has time to update the information from the repositories and notify you of any update.

---

