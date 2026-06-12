---
title: "Automatix doesnt work"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by baysl on 2007-01-30
When I try to install programs with automatix this error occurs:
FATAL ERROR
An apt-based error occured and installation was unsuccessful.

When I try to install with add/remove this occurs:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to
correct the problem.

---

### Post by Blutack on 2007-01-30
What happens if you open a terminal (Accessories --> Terminal) and type in
sudo dpkg --configure -a

---

### Post by baysl on 2007-01-30
This happens:
sudo dpkg --configure -a
Setting up java-common (0.25ubuntu1) ...
Setting up libltdl3 (1.5.22-4) ...
Setting up odbcinst1debian1 (2.2.11-13) ...
Setting up unixodbc (2.2.11-13) ...
roko@roko:~$ 

But automatix has the same error.

---

### Post by jackrobinson on 2007-01-30
what does
```
sudo apt-get -f install
```
give?

---

### Post by K.Mandla on 2007-01-30
You might do better to ask on the Automatix forums.

[http://www.getautomatix.com/forum/](http://www.getautomatix.com/forum/)

---

