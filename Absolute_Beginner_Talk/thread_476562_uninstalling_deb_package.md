---
title: "uninstalling deb package"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Irti on 2007-06-17
how can i uninstall a .deb package.......???? i installed opera for a 64 bit version and now opera shows up in my menu but does not run....its not there in synaptics and neither in add/remove.........same problem with avant-windows-navigator....i thought i wpuld uninstall them and then try to install it again........also i used kilz method to install firefox...... [http://ubuntuforums.org/showthread.php?t=202537&highlight=HOW+TO%3A+32+bit+firefox](http://ubuntuforums.org/showthread.php?t=202537&highlight=HOW+TO%3A+32+bit+firefox) 
but then i got flash and java running in my 64 bit version........how do i get rid of all the java and the flash packages i installed for the 32 bit....????????

---

### Post by meborc on 2007-06-17
to uninstall a deb package:

sudo dpkg -r <package name>

also you should be able to find it from synaptic and remove it there :)

---

### Post by steveneddy on 2007-06-17
> **meborc said:**
> 

also you should be able to find it from synaptic and remove it there :)

Only if you installed it through Synaptic I believe.

---

### Post by meborc on 2007-06-17
> **steveneddy said:**
> Only if you installed it through Synaptic I believe.

hmm... i see all my programs in synaptic... even the ones i have installed via dpkg -i :D ... might be my synaptic is magical... or might be i used apt-get -f install to get the dependencied sorted for my debs... ahh, where is the wisdom when you need it

str: 18
int: 3

---

### Post by Irti on 2007-06-17
nice....i removed opera.....but i still dont know how to remove avant windows navigator.....seriously it doesnt show up either in synaptics or add/remove........how do i uninstall it???????

---

