---
title: "error installing k3b"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by timo_01 on 2007-03-03
hi everyone.
am trying to install K3b using this command "sudo aptitude install k3b" but i get this error 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "
and i get "dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree"

i will be thankfull for any help

---

### Post by picpak on 2007-03-03
Run

```
sudo dpkg --configure -a
```

---

### Post by taurus on 2007-03-03
```
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude install k3b
```

---

