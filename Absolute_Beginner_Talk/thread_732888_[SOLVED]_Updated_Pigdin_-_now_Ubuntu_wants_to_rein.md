---
title: "[SOLVED] Updated Pigdin - now Ubuntu wants to reinstall the old version in the Update"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by zoopzoop on 2008-03-23
I installed the latest version of Pidgin (2.4.0) instead of the version that comes with Ubuntu (2.2.1) according to this tutorial: [http://ubuntuforums.org/showthread.php?t=658244](http://ubuntuforums.org/showthread.php?t=658244)
Everything worked fine but now the Ubuntu Update manager wants to "update" the Pidgin packages (pidgin, piding-data and libpurple0) back to the old versions (see screenshot).
I know that compiling a newer version from source does not really go hand in hand with Ubuntu's version management but it should at least notice that 2.4.0 > 2.2.1.
How can I tell Ubuntu to leave those packages alone?

---

### Post by Sef on 2008-03-23
Have you tried unclicking the check marks?

---

### Post by BandD on 2008-03-23
I had a similar issue when I installed a newer version of Open Office--it kept wanting to install the default Ubuntu version and I had a bunch of updates the system wanted to install.  I got around this by going into Synaptic and clicking on the package (in your case Pidgin 2.4.0) and going up to the Package menu at the top and clicking the box next to Lock Version.  That will force the system to use that version only.  If you want to update to a different version, you will probably have to uncheck that box first.  But anyway, that should fix the update problem.

---

### Post by zoopzoop on 2008-03-23
> **Sef said:**
> Have you tried unclicking the check marks?

Yes, but I was searching for an option to tell Ubuntu permanently not to try to update these packages.

Thanks, BandD, that did it for me!

---

