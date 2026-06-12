---
title: "Browse folders in root?"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-01-13
I want to add some GTK themes to my 
/usr/share/themes folder, but whenever I try add a file to the folder, the file manager throws them back at me. So my question is - How to browse folders in root? Or is that not my problem? IDK. :confused:

---

### Post by taurus on 2008-01-13
Applications -> Accessories -> Terminal
```
gksudo nautilus
```

---

### Post by yamfox on 2008-01-13
Wow! Quick! Thanks!

---

### Post by fiddledd on 2008-01-13
i thought all themes were stored themes in your Home folder, but to browse root folders/files use hir ALT-F2 and type "gksudo nautilus". But be very carefully as these files are protected from you for a reason. A deleted file here might mean you mess up your installation.


EDIT:
Everyone is quick except me, I type as if I got Boxing Gloves on so poat too late:)

---

### Post by zero-9376 on 2008-01-13
sudo apt-get install nautilus-gksu
gives you a right click option on folders and files to open as administrator - very handy!

---

### Post by overdrank on 2008-01-13
> **fiddledd said:**
> i thought all themes were stored themes in your Home folder, but to browse root folders/files use hir ALT-F2 and type "gksudo nautilus". But be very carefully as these files are protected from you for a reason. A deleted file here might mean you mess up your installation.


EDIT:
Everyone is quick except me, I type as if I got Boxing Gloves on so poat too late:)

Well you can take of the boxing gloves and have the answer saved to a text file for copy and paste lol :roll:

---

### Post by peterthewolf on 2008-01-13
zero
you should also say reboot before option appears

---

### Post by runemaste644 on 2008-01-13
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo nautilus
```
Huh? I always remember it being gksu. Also, you can always press Alt+F2 if you dont want a console open.

---

### Post by aysiu on 2008-01-13
> **runemaste644 said:**
> Huh? I always remember it being gksu. Also, you can always press Alt+F2 if you dont want a console open.
*gksudo* and *gksu* are the same thing.

---

