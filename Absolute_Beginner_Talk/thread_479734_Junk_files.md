---
title: "Junk files"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by thelemech on 2007-06-20
In Windows I was constantly using programs like Ccleaner and Clean Disk Security - to keep the junk down and keep the system more stable- is this annoying time consuming activity necessary in Ubuntu - or is Linux so different that any longtime users are now LOL:p

---

### Post by Inxsible on 2007-06-20
> **thelemech said:**
> In Windows I was constantly using programs like Ccleaner and Clean Disk Security - to keep the junk down and keep the system more stable- is this annoying time consuming activity necessary in Ubuntu - or is Linux so different that any longtime users are now LOL:p
 
you dont really need those programs in Linux. But if you would really like to get rid of packages that you no longer need, have a look into deborphan. There are a few others as well
 
I am not sure if its in the reps but if it is, you can install it by
 
```
sudo aptitude install deborphan
```

---

### Post by Inxsible on 2007-06-20
As a warning....
 
Be very careful while using Deborphan, as it can nuke your installation files too. Make sure you know what you are doing before using it.
 
If you are very new to Linux, I would suggest staying away from *all* cleaner utilities for a while until you better understand the workings of Linux

---

### Post by thelemech on 2007-06-20
Thanx- and yes I am new to Ubuntu - in fact have only used one other Linux distro, Suse 6 and that was some time ago.

---

### Post by FleetAdmiral74 on 2007-06-20
The only thing I can think of is some command like 

sudo apt-get clean 

or something like that, my impression was it checked for useless packages and cleared them or soemthing. But I think synaptic already deals with that, which by itself, by tracking dependencies, saves you a LOT of trouble watching what goes where and if it is needed.

---

### Post by Inxsible on 2007-06-20
> **FleetAdmiral74 said:**
> The only thing I can think of is some command like 
 
sudo apt-get clean 
 
or something like that, my impression was it checked for useless packages and cleared them or soemthing. But I think synaptic already deals with that, which by itself, by tracking dependencies, saves you a LOT of trouble watching what goes where and if it is needed.
 
You are probably thinking of 
 
```
sudo apt-get remove autoclean
```

---

