---
title: "Dependencies question"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by ArthurHeng on 2005-09-28
While installing dependencies for a certain application, do we need to also install the dependencies for the dependencies? If you know what I mean.

---

### Post by aysiu on 2005-09-28
Yes, but Synaptic/apt-get usually takes care of that.

---

### Post by ArthurHeng on 2005-09-29
OMG... Now Im manually downloading .deb's from packages.ubuntu.com, coz I need to backup .deb's in a disc to install in pcs without internet access. Is there a less painful way of getting all those debs plus their dependencies? Since once you install an application, apt-get will not re-download the packages again. Thanks in advance.

---

### Post by doclivingston on 2005-09-29
Running ```
apt-get --print-uris install packagename
``` will print out a list of all the packages that it needs to install, including dependencies.

---

### Post by ArthurHeng on 2005-09-29
Thanks, but my application's already the latest version, like the system told me, so it wont print the package and dependencies.

---

### Post by aysiu on 2005-09-29
[QUOTE=ArthurHeng]Thanks, but my application's already the latest version, like the system told me, so it wont print the package and dependencies.[/QUOTE] If you just want to know what the dependencies are, you can [right-click the application name](http://i22.photobucket.com/albums/b337/psychocats/609bb8d3.png) in Synaptic and then [go to the dependencies](http://i22.photobucket.com/albums/b337/psychocats/b070d780.png) tab to see what its dependencies are.

---

### Post by ArthurHeng on 2005-09-29
Actually I know the dependencies, packages.ubuntu.com already listed them out nicely for me, the problem is getting all of them. So I also need apt-get to get them all for me.

---

