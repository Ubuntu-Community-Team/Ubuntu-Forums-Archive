---
title: "Installing Lc3 simulator"
date: 2008-07-03
forum: Beginner Team
---

### Post by amsterdam63 on 2008-07-03
I have a folder on my desktop called lc3tools. I'm trying to figure out how to actually get the lc3 simulator installed so I can use it. The folder has a readme file that says this:

The LC-3 tools package is designed to work as either a personal or 
administrative installation on various flavors of Unix, including
Windows NT-based systems with appropriate support (e.g., Cygwin).

First, decide where the binaries and LC-3 OS code should be installed.
    * If you want it in the directory in which you unpacked the code,
      simply type "configure."
    * If you want it in a different directory, say /usr/bin, type
      configure --installdir /usr/bin
      replacing /usr/bin with the desired directory.

Then type 'make'.

If you want to make the tools available to other people, next type
'make install'.  If not, don't.

Please send any comments or bug reports to me at [email]lumetta@uiuc.edu[/email].
Unfortunately, due to the volume of e-mail that I receive on a regular
basis, I cannot guarantee that I will respond to your mail, but
I will almost definitely read it.

The folder contains these files:
CHANGE_LOG, configure, COPYING, lc3.def, lc3.f, lc3convert.f, lc3os.asm, lc3sim.c, lc3sim.h, lc3sim-tk.def, makefile.def, NO_WARRANTY, README, symbol.c, and symbol.h

---

### Post by DaEMoN390 on 2009-01-17
*bump

I'm also trying to install an LC3 simulator. I'm using 8.04 and I have tried several methods.
I know how to install applications via the terminal but, when trying to run the configure file for LC3TOOLS I get a permission denied error. I tried doing this in a sudo shell with still the same error. Another LC3 simulator I tried installing was the simplc simulator. This one installed fine but, the bash command for the UI isn't recognized. Any direction is appreciated.

---

### Post by overdrank on 2009-01-17
> **DaEMoN390 said:**
> *bump

I'm also trying to install an LC3 simulator. I'm using 8.04 and I have tried several methods.
I know how to install applications via the terminal but, when trying to run the configure file for LC3TOOLS I get a permission denied error. I tried doing this in a sudo shell with still the same error. Another LC3 simulator I tried installing was the simplc simulator. This one installed fine but, the bash command for the UI isn't recognized. Any direction is appreciated.

Hi and I would encourage you to start a new thread [Here]("http://ubuntuforums.org/forumdisplay.php?f=326")
As this is the Beginners team forum. :) not for support

---

