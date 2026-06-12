---
title: "how to run a bin file"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by mrpacman on 2008-02-09
dwnloaded google earth.bin to desktop. how to run it

---

### Post by Rocket2DMn on 2008-02-09
First change to the desktop in terminal, set executable permissions, then run
```
cd ~/Desktop
chmod +x earth.bin
./earth.bin
```

---

### Post by neurostu on 2008-02-09
try ./earth.bin

---

### Post by mrpacman on 2008-02-09
neither of two worked. bash: ./earth.bin no such file or directory  Thanks

---

### Post by Rocket2DMn on 2008-02-09
you need to use the full name of the file.  If it is "Google Earth.bin" you need to run
```
chmod +x Google\ Earth.bin
./Google\ Earth.bin
```
Note the \ before the space.  Once executable permissions are assigned, you can just double click the icon, too.

---

### Post by spiderbatdad on 2008-02-09
sh GoogleEarthLinux.bin

---

