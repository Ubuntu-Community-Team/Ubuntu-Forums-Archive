---
title: "Synaptic Package Manager"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by DaOg75 on 2006-06-26
Hi to all,  
i have a problem with the synaptic package manager that seems to have started after i upgraded to dapper from breezy. i have been trying to remove firestarter and i get the error msg:
 
[COLOR="Red"]E: /var/cache/apt/archives/firestarter_1.0.3-1.1ubuntu4_i386.deb: subprocess new pre-removal script returned error exit status 3
[/COLOR]

if i try to install anything or uninstall i get this error. i have tryed to delete the package in the archive directory mentioned in the error but this does not help. it seems no matter what i try dpkg still insists that i should reinstall firestarter and that it cannot remove it till i do. when i try to remove it from a terminal i get the following error:

#dpkg -r firestarter
dpkg: error processing firestarter (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
firestarter

so iam stummped and could use some help or direction. ](*,) i'll try to attach a shot of the desktop error:

---

### Post by nanotube on 2006-06-26
so, why don't you try reinstalling the package, just like the error messages keep telling you? reinstall, then uninstall.
and you might have better luck if you use aptitude (it generally does better at solving little problems like that.)
so
```
sudo aptitude reinstall firestarter
sudo aptitude remove firestarter
```

---

### Post by DaOg75 on 2006-06-26
thanks for the info on aptitude, i'll do some more research on that command. i was just using dpkg and synaptic. i tryed using aptitude and this is what i got:

og@DarkWing:~$ sudo aptitude reinstall firestarter
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

and when i try to remove i get:

og@DarkWing:~$ sudo aptitude remove firestarter
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

i tryed to run : dpkg --configure -a, like it says but it doesnt seem to do anything. at any rate thanks again for the help.

---

