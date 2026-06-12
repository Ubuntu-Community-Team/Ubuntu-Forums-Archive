---
title: "G5 installation"
date: 2011-03-04
forum: Apple Hardware Users
---

### Post by pauljwells on 2011-03-04
Hello Forum!

In a moment of madness I picked up a G5 dual core PowerMac from eBay for peanuts :)

I'm now wondering about how to get linux on it. Obviously, I'd prefer Ubuntu, but I think the ppc builds are 32 bit whereas YDL have a 64 bit version, but with ancient packages (Python 2.4 for example)

Should I worry? I have about 6GB of RAM lying around that I can fit. Will Ubuntu 32 bit see all of it?

Once the thing arrives I'll try all this out for myself but if anyone has already been here I'd like to hear...

I want to use the mac for python and f2py fortran development so I'm not worried about graphics support, wifi, all the tricky stuff, but it would be nice to be able to apt-get numpy, scipy etc rather than have to build everything from scratch. I'd be posting in Gentoo otherwise :-D

Awaiting your wisdom

---

### Post by Colin Rovis on 2011-03-05
I think, you should give it a try. Ubuntu 32bit will most likely recognize your 6GB RAM, and it will not be substantially slower then a 64bit-System, I think.

---

### Post by pauljwells on 2011-03-05
64 bit YDL downloaded (3.4GB - took ages...) and Ubuntu ppc downloading now.
The beauty of Linux is that I can try both! I'll post my experiences if anybody's interested.

---

### Post by pauljwells on 2011-03-06
A bit more searching shows that there is a 64bit kernel in the ppc installer and that it has SMP support...
Looks like I'm sorted

---

### Post by pauljwells on 2011-03-12
Well, that was easy! I slotted the old HD from my dead PC into the second drive bay in the powermac and chose the option to 'use entire drive' in the installer.

Up and running, fully updated, all the python packages I need are in the repos and Eclipse/PyDev up and running! :)

---

