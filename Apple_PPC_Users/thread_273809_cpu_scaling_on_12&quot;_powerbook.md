---
title: "cpu scaling on 12&quot; powerbook"
date: 2006-10-08
forum: Apple PPC Users
---

### Post by techrush on 2006-10-08
Im trying to get cpu frequency scaling working on my 12" rev D 1.5ghz powerbook. Ive installed a few of these so called cpu scaling daemons such as powernowd,cpufreq and cpudyn.

The problem is none of them seem to work! or at least i dont know how to configure them to do what i want. My goal is for my system to run cool and quiet like in OS X. No matter what i have tried "cat /proc/cpuinfo" tells me that my cpu is running at 1.5ghz as done the frequency scaling applet in the gnome toolbar. 


If anyone has any help or suggestions they could offer id appreciate it!

thanks.

---

### Post by APU on 2006-10-09
I have exactly the same PowerBook model and CPU frequency scaling worked out of the box after the installation of Dapper Drake. It switches between 749 Mhz and 1500 Mhz depending on the CPU load. Maybe uninstalling all daemons you installed will restore this behaviour?

And Ubuntu _does_ run the PowerBook a bit hotter than OS X, even with active frequency scaling!

---

### Post by techrush on 2006-10-09
a recent set of updates fixed it apparently as its now working properly. ive got just about evertything working how i want on this laptop now. its even running OS X with mac on linux. :)

---

### Post by stmiller on 2006-10-09
Does sleep or hibernate work on your powerbook?

---

### Post by APU on 2006-10-10
Currently Sleep/Hibernate cannot work with this PowerBook because of the graphics chipset which there are no suitable  PPC drivers available for.

Suspend to Disk also doesn´t work with the current Ubuntu Kernels, but I got it working with self compiled 2.6.17 and 2.6.18 kernels already. Probably this will be "officially" working with the next Ubuntu release (Edgy Eft) later this month but there are still some serious problems left!

Look at this thread for details: 

[http://ubuntuforums.org/showthread.php?t=248889](http://ubuntuforums.org/showthread.php?t=248889)

---

