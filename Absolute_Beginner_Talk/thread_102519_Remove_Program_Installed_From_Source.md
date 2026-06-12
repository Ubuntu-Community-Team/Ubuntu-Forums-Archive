---
title: "Remove Program Installed From Source"
date: 2005-12-12
forum: Absolute Beginner Talk
---

### Post by twshelton on 2005-12-12
I installed Subversion from source in order to compile the SWIG bindings for my server.  I was not able to get SWIG operational and now neew to remove Subversion from my system and install from apt-get.  The problem is that if I attempt to execute "make uninstall" as has been suggested, it errors out.  

Any help in removing and reinstalling would be greatly appreciated.

Regards,
Thomas

---

### Post by alynx on 2005-12-12
sudo apt-get remove <name of program / package>

is that working ?

good luck mate

---

### Post by MartinG on 2005-12-12
sudo apt-get remove <name of program / package> will only work if you installed via a .deb.  The usual "configure, make, make install" doesn't do so, and in theory you're left to chase down the individual files -- nightmare!

There is however a "cheat".  First, install "checkinstall" and any dependencies from synaptic. Then, repeat your original installation exactly as you did it before, BUT replace "make install" with "checkinstall".  This will then build your application into a deb file, and install it, in the process overwriting all the files from your first install.  But because it was done from a deb, you can now use synaptic or apt-get to uninstall, and it will do the work for you.

In fact as a general rule I'd suggest you always try to use checkinstall when installing from source, for ease of uninstalling.

---

### Post by twshelton on 2005-12-12
Exactly what I was looking for.  

Thanks MartinG.  I'll give it a shot and let you know if I have any other problems.

---

### Post by twshelton on 2005-12-12
Looks like it worked.  There was a symbolic link left over that was causing some issues.  after I did the checkinstall, then removed using dpkg -r, I installed using apt-get.  Then when I typed svn --version, it was pointing to the old location.  After a few minutes of attempting to correct, I simply created a new symbolic link to the location the old one was looking for....it now works.

Thanks again...this is a great little tool for newbies and should be added to the Ubuntu Guide.

---

