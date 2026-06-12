---
title: "kdelibs4c2 configuration"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by silent_enigma on 2006-04-14
i wanna install kpackage 
[PHP]sudo dpkg -i kpackage_3.4.3-0ubuntu1_i386.deb[/PHP]

it gave some errors of missing librarys and kdelibs4c2
so i downloaded them from :[http://packages.ubuntu.org/](http://packages.ubuntu.org/)
but while installing kdelibs4c2 and kdelibs-bin
they both gives the same error :

[PHP]Unpacking replacement kdelibs4c2 ...
dpkg: dependency problems prevent configuration of kdelibs4c2:
 kdelibs4c2 depends on kdelibs-bin (= 4:3.4.3-0ubuntu2); however:
  Package [COLOR="Red"]kdelibs-bin is not configured yet[/COLOR].
dpkg: error processing kdelibs4c2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdelibs4c2
[/PHP]

and kdelibs-bin give this error:

[PHP](Reading database ... 63107 files and directories currently installed.)
Preparing to replace kdelibs-bin 4:3.4.3-0ubuntu2 (using kdelibs-bin_3.4.3-0ubuntu2_i386.deb) ...
Unpacking replacement kdelibs-bin ...
dpkg: dependency problems prevent configuration of kdelibs-bin:
 kdelibs-bin depends on kdelibs4c2 (>= 4:3.4.3); however:
  Package [COLOR="Red"]kdelibs4c2 is not configured yet[/COLOR].
dpkg: error processing kdelibs-bin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kdelibs-bin
[/PHP]

i couldnt find how to configure it??
or installl

---

### Post by Ferri on 2006-04-14
Have you tried (from command-line)?```
sudo apt-get install kpackage
```
It should resolve the dependencies of the package and install them.

---

### Post by silent_enigma on 2006-04-14
:D dude  i know it but i cant get that like you posted in ur msg.
i connect internet from school and i cant use that functions and synaptics :(

---

