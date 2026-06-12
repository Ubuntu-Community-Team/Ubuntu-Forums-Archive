---
title: "gdm and kdm"
date: 2006-01-10
forum: Absolute Beginner Talk
---

### Post by IronToad on 2006-01-10
I have Kubuntu desktop with gdm logon screen and how do I do to change the login screen to Kdm?
/Thanks

---

### Post by patrick295767 on 2006-01-10
[QUOTE=IronToad]I have Kubuntu desktop with gdm logon screen and how do I do to change the login screen to Kdm?
/Thanks[/QUOTE]
  
I dont know ...
 
Sthg working, 
```
apt-get remove gdm
apt-get -f install kdm
```  
  
Greetings,

Patrick

---

### Post by aysiu on 2006-01-10
Alt-F2 ```
kdesu konqueror
``` Go to /etc/X11 and look for something with a name like *default-display-manager* and change it from /usr/sbin/gdm to /usr/bin/kdm

---

### Post by Adrian on 2006-01-10
[QUOTE=IronToad]I have Kubuntu desktop with gdm logon screen and how do I do to change the login screen to Kdm?
/Thanks[/QUOTE]

Make sure that kdm is installed. Then, try this:
```
sudo dpkg-reconfigure kdm
```

---

### Post by estel on 2006-01-10
Go for the latter.

---

