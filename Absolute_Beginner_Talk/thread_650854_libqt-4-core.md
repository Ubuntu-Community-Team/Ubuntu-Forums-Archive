---
title: "libqt-4-core"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by AI13 on 2007-12-26
Ok, so I seem to be having problems with meeting dependencies. This is the most recent one, so, what exactly is this(libqt-4-core), and what does this mean "Dependency not satisfiable, libqt-4-core?" I was trying to install skype from [http://www.skype.com/intl/en/download/skype/linux/beta/choose/](http://www.skype.com/intl/en/download/skype/linux/beta/choose/)
Thanks  

ps.

please forgive my ignorance.

---

### Post by Hospadar on 2007-12-26
you should try installing skype from medibuntu
Here's how to add the repos:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then go into synaptic, click "Reload" search for skype and install.

I'm gonna guess the problem is that it's looking for "libqt-4-core" and not "libqt4-core" it's a minor issue that if you really wanted you could fix yourself by changing the dependency list inside the package, but it's much easier to use medibuntu.

---

### Post by AI13 on 2007-12-26
From there I got:

skype:
 Depends: libqt4-core (>=4.3.2) but it is not installable
 Depends: libqt4-gui (>=4.3.2) but it is not installable
 Depends: dbus-x11 (>=1.0.0) but it is not installable

---

### Post by Hospadar on 2007-12-26
what version of ubuntu are you running?  I'm in 7.10 and looking at my synaptic right now and those are the versions I have installed.  If you are using feisty or something older, you may need to go into the gutsy repositories and download and install the debs manually (no garuntee that will work, they may themselves have unsatisfied dependencies) or upgrade to 7.10

If you are using 7.10, make sure you are using the internet repos and not the CD System->Administration->Software Sources, uncheck "installable from CD" and check the three (or four?) repositories above that.  then go to a terminal and "sudo apt-get update"

If none of that is working, and you're feeling a bit hackish, get the version numbers for those packages that is installable (look in synaptic) then, manually download the skype .deb from medibuntu, go into it with "Archive Manager" (right click, open with->) extract it all out, you'll find a file that has a dependency list, change the version numbers in this list to the versions you have, repack the archive so it looks just like you found it, and install!  (Note! this is a pain in the ***, and may not work, but I've done it before and it's quite possible with a bit of patience, personally I think it'd be a better decision to make the move to 7.10 if you have to)

There's probably a better way to go about this, you might try installing the .rpm (redhat) with "alien" (sudo apt-get install alien), other than that though I'm not sure what you would do.

---

