---
title: "Freenx on Edgy PPC?"
date: 2007-04-11
forum: Apple PPC Users
---

### Post by marcus2004 on 2007-04-11
I am just wondering if anyone has installed freenx server on their ppc for edgy and how they did it.

Is there a good source list for ppc that includes freenx? Or a .deb would help as well. 
I am fairly familiar with ubuntu just not on a ppc.

---

### Post by fkdev on 2007-04-12
I tried it once, I think. Compiled fine, though I never bothered to set it up.
Get freenx at: [http://prdownload.berlios.de/freenx/freenx-0.6.0.tar.gz](http://prdownload.berlios.de/freenx/freenx-0.6.0.tar.gz)
Most of the software is actually from nomachine, which you get at [http://www.nomachine.com/sources.php](http://www.nomachine.com/sources.php)
looking at a gentoo ebuild, you'll probably need:
nx-X11, nxagent, nxauth, nxcomp, nxcompext, and nxproxy ( not in that order )
and the versions of ( including -dev packages) (note these don't match up to ubuntu packages ):
libpng, libxpm, jpeg, zlib, libXdmcp, imake, gccmakedep
Just download sources, build, and apt-cache search for other dependencies.
Then install freenx.

---

### Post by marcus2004 on 2007-04-13
Sounds good. Thank you for your help.

---

