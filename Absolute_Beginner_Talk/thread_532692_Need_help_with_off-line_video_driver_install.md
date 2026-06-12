---
title: "Need help with off-line video driver install"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by anewguy on 2007-08-23
I know there are TONS of questions on this forum about video problems - so far I've seen where the Envy tool works good for things like the NVidia drivers.  I was given an older PIII-500 desktop that has a Riva TNT card with 32 meg.   The problem is that there is no internet connection available on the computer - it doesn't have an ethernet adaptor or a wireless adaptor.  So, is there a way to install the nVidia driver for this card by downloading things to my laptop (all Ubuntu 7.04) and copying to cd to install on the desktop computer?  Any help would be greatly appreciated, and I apologize for another video question!:)

---

### Post by RomeReactor on 2007-08-23
Hi. You could grab the **nvidia-glx-legacy** package from [packages.ubuntu.com]("http://packages.ubuntu.com/feisty/misc/nvidia-glx-legacy"); Just make sure you have the dependencies installed--search Synaptic for the packages marked in red in that page. If you don't have some of them, you'll need to download and install those, along with their own dependencies, before installing the drivers. Double-click on the .deb files to install, and remember to install dependencies before the packages that require them.

Or, if you don't need direct rendering on the PIII, just use the **nv** driver that installs by default.

**EDIT**: An easier way is to use Synaptic on the PIII, search for **nvidia-glx-legacy**, mark it for installation, then--still in Synaptic--go to "File->Generate package download script". Copy that script to one of your Ubuntu machines with internet access, and run the script, then copy the downloaded files to the PIII. Once there, in Synaptic go to "File->Add downloaded packages".

---

### Post by anewguy on 2007-08-23
Thanks - I'll give the legacy drivers a try!:)

---

