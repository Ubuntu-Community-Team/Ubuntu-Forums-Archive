---
title: "Where have all the synaptic apps gone"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-05
Where has wine and amsn gone?
I still dont understand how to install applications that dont appear in synaptic archives, as there seems to be so many releases for everything (and i dont just mean the linux dist) when i do unpack the .tar file there seems to be .deb .bin .this .that. Is there any kind of runtime and installation standard? Where do all the program's files go. (like in windows theres 'program files')

---

### Post by Ampersand on 2005-10-05
Firstly, have you got all of the synaptic repositories enabled (universe and multiverse)? Instructions for adding these can be found here: [http://www.ubuntuguide.org/#repositories](http://www.ubuntuguide.org/#repositories). 

The method of installing software that isn't in the repositories varies, and should be documented in a file called 'install' when you extract the package. Generally, you will have to compile it. Get the 'build-essential' package from synaptic, this will install the necessary tools. You will then have to open a terminal, change directory to the folder containing the program to be installed, then run './configure' followed by 'make' and finally 'make install'.

Unfortunately, you will have to install the libraries that the program depends on as well. These can usually be installed through synaptic. Make sure you get the packages ending in '-dev'.

---

### Post by drgreborn on 2005-10-05
i believe win e and amsn is in backport and thus no longer available? Correct me if I'm wrong. For wine you can add your own repository into source.list. They are as follows:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

---

### Post by Ampersand on 2005-10-05
Amsn is in the Breezy repositories, so it should also be in the backports ([https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports), the mirrormax ones are no longer available).

---

### Post by dgrafix on 2005-10-05
i tried that deb-src (url) command and it said command not found

---

### Post by dgrafix on 2005-10-05
ah ok, i get it thanks!

---

