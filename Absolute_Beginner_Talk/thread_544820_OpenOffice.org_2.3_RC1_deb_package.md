---
title: "OpenOffice.org 2.3 RC1 deb package"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by lamarcheb on 2007-09-06
The openoffice.org community has released deb packages for the 2.3 RC1. I think its a first.

I've downloaded the archive and extracted it and as expected the folder contains several deb files. However how do I install it? Each time I start to install a deb it says the dependencies are not satisfiable.   I started with openoffice.org-core-01.deb. I tried all of them and I get the same message.

The Ubuntu office.org packages were first uninstalled fully using apt-get remove office.org-core.

Any advice would be appreciated

:confused:

---

### Post by SOULRiDER on 2007-09-06
Do they list what dependency they are missing?

---

### Post by deadgobby on 2007-09-06
Why are you not installing using synaptic?

---

### Post by lamarcheb on 2007-09-07
SOULRiDER: For missing dependencies, it always lists one of other uninstalled deb files. For instance, if I try openoffice.org-core-01.deb, it will say something like that dependencies are in openoffice.org-core-02.deb. I tried installing them recursively with no success.

deadgobby: That's the point, these are standalone debs downloaded from the openoffice.org web site, and not on any repositories. Or am I missing something, can I use Synaptic (or apt) for local debs, and if so, how?

---

### Post by eapache on 2007-09-07
The packages are cross-dependent (a depends on b and b depends on a). I don't know how to fix it, but I have the same problem with the pidgin and pidgin-data packages from getdeb.com

---

### Post by stchman on 2007-09-07
> **lamarcheb said:**
> The openoffice.org community has released deb packages for the 2.3 RC1. I think its a first.

I've downloaded the archive and extracted it and as expected the folder contains several deb files. However how do I install it? Each time I start to install a deb it says the dependencies are not satisfiable.   I started with openoffice.org-core-01.deb. I tried all of them and I get the same message.

The Ubuntu office.org packages were first uninstalled fully using apt-get remove office.org-core.

Any advice would be appreciated

:confused:

Try this.  Go to the folder that has all the .deb files and type this:

```
sudo dpkg -i *.deb
```

Let us know if that worked.

---

### Post by lamarcheb on 2007-09-07
eapache: Hey dude, I used to live in Ottawa! All my relatives are there. Now I live in Houston, TX.

stchman: Thanks. I'll try it in a minute ... How was I supposed to figure this out!?

---

### Post by lamarcheb on 2007-09-07
stchman: Thank you sir! It works!:popcorn:

For the desktop integration, however, I had to run the deb manually since it was in a sub-folder.

Starts up with the Tango toolbars icons. New chart engine. Report writer. Cool.

---

