---
title: "Asus repository problem"
date: 2012-10-11
forum: Asus Ubuntu Support (CLOSED)
---

### Post by awambawamb on 2012-10-11
Hi there,
i got a problem with the update manager while upgrading... i'll try to explain the problem as good as i can!

today day i've finally upgraded my asus eee 1015px (ubuntu certified) from the 10.10 to the 11.10.

everything went fine until I did the last update... that ruined asus repositories setup. as now, the update manager is searching the updates here:

[http://asus.archive.canonical.com/updates/dists/oneiric/](http://asus.archive.canonical.com/updates/dists/oneiric/)

but there's no such directory!

going through browser, i can see that [http://asus.archive.canonical.com/updates/](http://asus.archive.canonical.com/updates/) has more than one "oneiric" folder but every one is specific, with a name after it:

[DIR]	oneiric-beitou/
[DIR]	oneiric-boulder/
[DIR]	oneiric-dell/
[DIR]	oneiric-madou/
[DIR]	oneiric-nuannuan/
[DIR]	oneiric-sutton/
[DIR]	oneiric-tianjin/
[DIR]	oneiric-upton/
[DIR]	oneiric-xinbeitou/	 
[DIR]	oneiric-xizhi/

i wonder which one is the one that i have to set as my asus repository...

i think i've understood that in the GUI, the url has to be
[http://asus.archive.canonical.com/updates](http://asus.archive.canonical.com/updates)

then it automagically enters the folder
/dist/

then it chooses the "distribution" forlder, that in my case would be just
/oneiric/

and here comes the problem, since [http://asus.archive.canonical.com/updates/dists/oneiric/](http://asus.archive.canonical.com/updates/dists/oneiric/) doesn't exists.

anyone that could help me solve the problem? i've deactivated that repo for now, but i wouldn't like to miss some important asus-specified updates.

thanks for the attention!

---

### Post by oldos2er on 2012-10-11
Moved to Asus Ubuntu Support.

---

### Post by awambawamb on 2012-10-16
anyone out there to help me? this section is dead :(

---

### Post by awambawamb on 2012-10-22
...bump?

I would really appreciate if someone can tell me something about those repo that i had to disable... i wouldn't miss some updates from asus, if those are going to help keeping my netbook in a good state.

---

### Post by buckyaustin on 2012-10-22
The thing with Linux is, if you have it working chances are you shouldn't change it much. Be sure to keep everything backed up because when the next Ubuntu comes out I'm sure you are going to need to do a fresh install, which means wipping your whole system.

So from now on keep back ups of everything, and use a live cd to do the next distrobution upgrade.

---

