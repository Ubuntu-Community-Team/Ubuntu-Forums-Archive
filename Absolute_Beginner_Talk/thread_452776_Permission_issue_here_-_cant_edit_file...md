---
title: "Permission issue here - cant edit file.."
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by humbll on 2007-05-23
I have to edit a file in etc/apt but when i open it by double-clicking on it and then edit it, i am not allowed to save it. It says i do not have the permissions. I made myself a member of the ROOT group, still no dice. It is owned by ROOT, so is there a way to edit this file without having to log out and back on as ROOT? Perhaps with SUDO command? It is a hassle to log out, open all my browser windows again, as well as my programs i have running, etc. but if this is my only choice, so be it. thanks in advance..

---

### Post by annda on 2007-05-23
```
sudo gedit file_name
```

---

### Post by humbll on 2007-05-23
thank you, i new it had to be simple... i had tried sudo edit filt.xxx but it returned an error..thanks again..

---

