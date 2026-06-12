---
title: "Installing SlimServer"
date: 2007-01-14
forum: Absolute Beginner Talk
---

### Post by weirdlookinguy on 2007-01-14
Hey guys!  I've set up a server PC (P4 2.53Ghz,  512MB of RAM, its a modern PC) running Ubuntu 6.10.  I've gotten Apache Server installed, but I also want to install SlimServer to stream my music across the net.  However, when I go to install it (sudo apt-get install slimserver) this is what I get:

_____________________________________________________________________________
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  slimserver: Depends: libcgi-perl but it is not installable
              Depends: libclass-accessor-chained-perl but it is not installable
              Depends: libclass-data-inheritable-perl but it is not installable
              Depends: libclass-trigger-perl but it is not installable
              Depends: libclass-virtual-perl but it is not installable
              Depends: libclass-whitehole-perl but it is not installable
              Depends: libfile-which-perl but it is not installable
              Depends: libima-dbi-perl but it is not installable
              Depends: librpc-xml-perl but it is not installable
              Depends: libfile-slurp-perl but it is not installable
              Depends: libdata-page-perl but it is not installable
              Depends: libtie-regexphash-perl but it is not installable
              Depends: libpoe-perl but it is not installable
              Depends: libtime-modules-perl but it is not installable
              Depends: libuniversal-moniker-perl but it is not installable
              Depends: libcache-cache-perl but it is not installable
              Depends: libtext-unidecode-perl but it is not installable
              Depends: libtie-cache-perl but it is not installable
              Depends: liburi-find-perl but it is not installable
              Depends: liberror-perl but it is not installable
              Depends: libclass-singleton-perl but it is not installable
              Depends: libfile-find-rule-perl but it is not installable
              Depends: libxml-writer-perl but it is not installable
              Depends: sox but it is not installable
-------------------------------------------------------------------------

Do I need to install Perl?  Can anyone tell me how?  Thanks, Raul.

---

### Post by Marsolin on 2007-01-15
Do you have the universe and multiverse sections of the Ubuntu repositories enabled? If that doesn't work try installing one of those listed as uninstallable directly and it will give you more information regarding the problem.

---

### Post by weirdlookinguy on 2007-01-15
Hey, thanks for replying marsolin!  Unfortunately, I have no idea what universe and multiverse are, could you please explain?  Also, I tried going into terminal and typing "sudo apt-get install libcgi-perl" and it said the package is "not available, but is referred to by another package."

Help, anyone?

---

### Post by Marsolin on 2007-01-15
> **weirdlookinguy said:**
> Hey, thanks for replying marsolin!  Unfortunately, I have no idea what universe and multiverse are, could you please explain?  Also, I tried going into terminal and typing "sudo apt-get install libcgi-perl" and it said the package is "not available, but is referred to by another package."

Help, anyone?

It sounds like the repositories are your problem.  To enable them open Synaptic and select Repositories from the Settings menu.  See [here]("http://linuxappfinder.com/addrepo") for some screenshots.  Look for any lines that are grayed out, but list universe and multiverse in the sections column and enable them.  I'm not sure if if multiverse is in there by default, but you can add it every place that you see universe listed.  Just separate them by a space.

---

### Post by weirdlookinguy on 2007-01-18
Thanks man.  I ended up editing my sources.list and it did the trick.  Thanks

---

