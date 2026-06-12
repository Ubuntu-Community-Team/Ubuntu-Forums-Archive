---
title: "Upgrading from 8.04.2 to 8.10 error."
date: 2009-04-14
forum: Apple Hardware Users
---

### Post by blubaustin on 2009-04-14
Trying to upgrade from ubuntu 8.04.2 PPC to ubuntu 8.10 and encountered this error:

Unpacking amarok-common (from .../amarok-common_2%3a1.4.10-0ubuntu3.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/amarok-common_2%3a1.4.10-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/bin/amarok_daapserver.rb', which is also in package amarok
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/amarok-common_2%3a1.4.10-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am not going to restart because I'm afraid I won't be able to log back in, or something bad.
[IMG]http://i621.photobucket.com/albums/tt299/blubaustin/Screenshot.png[/IMG]

---

### Post by blubaustin on 2009-04-15
SOLVED:

sudo apt-get remove amarok

and everything updated...now a new error!

---

