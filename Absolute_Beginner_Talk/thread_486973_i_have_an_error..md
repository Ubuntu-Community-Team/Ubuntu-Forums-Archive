---
title: "i have an error."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by death_god on 2007-06-28
i tried to install my wireless driver and now every time i open the synaptic package manager i get this message E: The package bcm43xx-firmware needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

what can i do?

---

### Post by chandler on 2007-06-28
How did you install it?

---

### Post by death_god on 2007-06-28
GDebi package installer and now i can't instll anything

---

### Post by chandler on 2007-06-28
try```
sudo apt-get autoclean
```

You could try to save the file that you installed to your local drive then add the folder to /etc/sources.list

---

### Post by death_god on 2007-06-28
i keep getting the same message

---

### Post by Seisen on 2007-06-28
Try uninstalling it and than reinstalling it.

---

### Post by death_god on 2007-06-28
i'm a real newbie and i don't know how to uninstall anything

---

### Post by chandler on 2007-06-28
start synaptic and start typing in the name and you should see it there...  if you do, then uncheck the check mark or right click it then click uninstall..  if it doesn't show up then I don't know *doesn't hav the GUI in front of him*

---

### Post by death_god on 2007-06-28
problem is i can't start synaptic because i get this error E: The package bcm43xx-firmware needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
and when i try to install the package again, it tells me that the package is corrupted.

---

