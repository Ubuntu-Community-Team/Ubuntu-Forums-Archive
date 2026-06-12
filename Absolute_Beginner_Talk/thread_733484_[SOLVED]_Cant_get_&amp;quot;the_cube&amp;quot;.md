---
title: "[SOLVED] Cant get &amp;quot;the cube&amp;quot;"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Xxbrandnew10xX on 2008-03-23
Ive been reading and trying to get the compiz config setting manager to install but i cant figure it out i just want to be able to run the 3d cube effect and installing the manger looks like the only way so this is what it says after i type sudo aptitude install compizconfig-settings-manager ...
this is what i get
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



any help on what is wrong its a dv6000 laptop if that helps thanks

---

### Post by saj0577 on 2008-03-23
You got synaptic Package manager running? or another sudo apt-get running?

Saj

---

### Post by Wolfan on 2008-03-23
Seems you have something else open, try making sure everything is closed even to the point of restarting your computer, this happens sometimes when you have a version of synamptic package manager open and you try to install with another, (which I did a lot at first).

---

### Post by smartboyathome on 2008-03-23
Or it can be the update manager. Anything installing at all which is a deb package or from a repo will cause that error.

---

### Post by Xxbrandnew10xX on 2008-03-23
ok so i made sure everything is closed and i tried again and this is what it says...sudo aptitude install compizconfig-settings-manager
[sudo] password for brandon:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "compizconfig-settings-manager"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  


so it sounds like its not finding that particular package anyone know where i can get it thanks

---

### Post by 3rdalbum on 2008-03-23
You need to enable the Universe repository.

System > Administration > Software Sources

Put a tick in all the checkboxes underneath "Downloadable from the Internet".

When it asks you if you want to reload the package list, click OK.

---

### Post by smartboyathome on 2008-03-23
Check to see if Universe is enabled (System > Administration > Software sources). It is in that, not the Main repository.

---

### Post by joshrobinson on 2008-03-23
in synaptic, what repo's do you have enabled? on the first tab make sure everything but source is checked, and on the second the first one checked
```
sudo apt-get update
```
then 
```
sudo apt-get install compizconfig-settings-manager
```

it should be there, if you have too you can download the package and install it manually, but im not sure of its dependencies and if you have them

---

### Post by Xxbrandnew10xX on 2008-03-23
thank you that did it

---

### Post by smartboyathome on 2008-03-23
Please mark the thread as solved (Thread Tools > Mark thread as solved)

---

