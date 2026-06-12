---
title: "Clean up Kubuntu packages"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-02-15
So i've recently installed the kubuntu-desktop package to fool around with, and after deciding i didn't much like it, i've decided to uninstall and go back to gnome.

Is there an easy way for me to uninstall all the apps that get installed WITH kubuntu-desktop? because it installs a ton of software when installed in synaptic, but when i go to uninstall it, it doesn't take those applications with it.

---

### Post by skyhopper88 on 2007-02-15
Well, since you used synaptic you'll have to remove it all one by one (so to speak). From Gnome, follow the long directions for removing Kubuntu here
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by sunexplodes on 2007-02-15
oh my god, for some reason the command at that site is removing a lot more than the command asks for... i've lost:

quod libet
ipod stuff
k3b
build-essential
gnome-splashscreen-manager
gstreamer
totem
gnumeric

among a ton of other stuff i don't even know about. zoinks.

---

### Post by skyhopper88 on 2007-02-15
Oh...crap...Are you on Dapper or Edgy? The commands for Dapper are on a different page >_<

---

### Post by sunexplodes on 2007-02-15
No, i'm on Edgy, i saw that note on the page. Pretty weird stuff. Not too big a deal. I took note of the stuff it removed, so i can re-install the good stuff.

Just weird, is all.

---

### Post by Sklasko on 2007-02-15
On a side note, you'll likely want to use aptitude over apt-get or synaptic from now on. Aptitude is capable of keeping of with all the packages that get installed with metapackages and their dependencies.

---

