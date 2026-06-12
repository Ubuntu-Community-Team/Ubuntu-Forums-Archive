---
title: "Installed KDE but cannot getinto it"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by sankarv on 2006-09-18
I have installed KDE Desktop environment from ubuntu DVD onto my existing dapper Ubuntu system. But in the GDM i cannot see KDE as an option in session dialog.


How to add Kde?

---

### Post by sankarv on 2006-09-19
pls help

---

### Post by Perfect Storm on 2006-09-19
Did you:
```
sudo aptitude install kubuntu-desktop
```

---

### Post by sankarv on 2006-09-19
No. I just installed from synaptic" KDE Desktop Environment " thro DVD ubuntu

---

### Post by Perfect Storm on 2006-09-19
You shall run the above command as I shown. This will install all the right files to have a fully functunal KDE enviroment.
Like if you want XFCE you do;
```
sudo aptitude install xubuntu-desktop
```

---

### Post by sankarv on 2006-09-19
Does this need a net connection. I dont have it right now. But how can we install from DVD.

---

### Post by Perfect Storm on 2006-09-19
I don't know if kubuntu is on the DVD, but you can always try to see if the commands work.


Lets see if your DVD is listed in your sourcelist;
```
cat /etc/apt/sources.list
```

---

