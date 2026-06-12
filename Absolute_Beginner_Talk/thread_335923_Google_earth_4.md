---
title: "Google earth 4"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2007-01-10
I am trying to install the new google earth 4 but the linux package is .bin.  How would this be installed?

---

### Post by hanzomon4 on 2007-01-10
[list][*]chmod it to make it executable```
chmod 777 googleearth.bin
``` replace googleearth.bin with the name of the *.bin file[*]Then run it as sudo```
sudo ./googleearth.bin
```[/list]

---

### Post by taurus on 2007-01-10
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 **filename**.bin
./**filename**.bin
```

---

### Post by gentlemanmasher on 2007-01-11
I tried Taurus solution and it worked thanks both again for your help.  I really appreciate it.

---

