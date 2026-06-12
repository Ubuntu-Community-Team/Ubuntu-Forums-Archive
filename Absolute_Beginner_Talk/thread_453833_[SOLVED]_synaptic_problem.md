---
title: "[SOLVED] synaptic problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by k33bz on 2007-05-24
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and when i run that command i get this

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring openttd &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; You need to install data files                                            &#9474;  
 &#9474;                                                                           &#9474;  
 &#9474; OpenTTD needs the data files from the original Transport Tycoon Deluxe    &#9474;  
 &#9474; game to run. You should install these data files before you can play the  &#9474;  
 &#9474; game. See README.Debian for more details on which files need to be        &#9474;  
 &#9474; copied where.   

how do i get rid of this, i dont have the files for it, so i want to get rid of the installation

---

### Post by Hobo Joe on 2007-05-24
```
sudo aptitude purge <program name>
```

---

### Post by alienexplorers on 2007-05-24
run 
> sudo dpkg --configure -a
in the terminal

---

### Post by Hobo Joe on 2007-05-24
> **alienexplorers said:**
> run 

in the terminal

He did, that's the output of it that he posted....

---

### Post by k33bz on 2007-05-24
didnt work i got this

k33bz@treehouse:~$ sudo aptitude purge OpenTTD
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
k33bz@treehouse:~$

---

### Post by k33bz on 2007-05-24
waht would happen if i just remove the directory that the game started to install in

---

### Post by k33bz on 2007-05-24
ok that just answered my question, that didnt work as well,

anyone have any ideas

---

### Post by k33bz on 2007-05-24
mmm, nvm, i guess that did work after all

---

