---
title: "How to set a script to run at boot up in ubuntu"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by vanthai26 on 2006-09-11
Hi 

Does any one know how to set up ubuntu so that I can get a script to start up at boot time and set run level as well Thanks I am new to ubuntu


Bar

---

### Post by frodon on 2006-09-12
Create your script, give it execute rights and put it in /etc/init.d, then run this command :
```
sudo update-rc.d *name_of_your_script* defaults
```That's all.

---

### Post by Najand on 2006-09-12
> **frodon said:**
> Create your script, give it execute rights and put it in /etc/init.d, then run this command :
```
sudo update-rc.d *name_of_your_script* defaults
```That's all.
If it is a module, add it to *[FONT="Courier New"]/etc/module[/FONT]* using:
```
sudo echo MODULENAME >> /etc/module
```

---

