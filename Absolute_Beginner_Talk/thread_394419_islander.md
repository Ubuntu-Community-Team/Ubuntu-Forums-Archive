---
title: "islander"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by islander on 2007-03-26
while downloading updates I received this notice : an error occurred E:dpkg was interrupted ,you must manually run dpkg --configure-a to correct the problem .
Looking for help ?
islander

---

### Post by Sandlst on 2007-03-26
Try opening a terminal (Applications/Accessories/Terminal) and copying this in:```
sudo dpkg --configure -a
```Then you may have to run the update again```
sudo apt-get upgrade
```Hope this helps, post back if you have any problems!

---

### Post by islander on 2007-03-27
thanks Sandlst  your help worked out fine !
Islander

---

