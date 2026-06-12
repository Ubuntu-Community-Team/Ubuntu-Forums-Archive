---
title: "transcode, gmplayer compiling problems in iBook G4"
date: 2005-04-14
forum: Apple PPC Users
---

### Post by Liakoni on 2005-04-14
Has anyone tried successfully to compile transcode?
I had no problems in configure, but i got errors in make.

The same with mplayer.
In configure with --enable-gui i have no problems, but i get error messages in make.

I am using 
iBook g4 1,33MHz
768 MB RAM
ATI 9200 32 MB

---

### Post by pvz on 2005-04-14
I ran in the same problem recently with the same iBook. The Mplayer-g4 package from the universe repository is just an empty shell without a binary, and transcode has no .deb, but is in the repository as a tarball. So I tried to install Mplayer and transcode from [http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/mplayer/](http://honk.physik.uni-konstanz.de/~agx/linux-ppc/debian/mplayer/)
but that repository has dependency problems with hoary.
Compiling Mplayer failed with a bad pointer something error, haven't tried transcode yet. Both packages were in the repositories before and installed fine, but something has changed after hoary final, it seems.

---

