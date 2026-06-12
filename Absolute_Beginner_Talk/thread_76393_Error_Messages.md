---
title: "Error Messages"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by tay on 2005-10-15
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

it was alot longer, but i think somebody will know what i'm saying.

i typed apt-get install firestarter

also when i want to apt-get install packages that are on my desktop
do i use the same name as the package?  for example i have an apache package apache2 2.0.50.orig.tar.gz

it is listed as apache2 2.050 in the archives..

I tried apt-get install with both names and neither worked.

also i get this one after apt-get update

W: Couldn't stat source package list [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

so what is happening?

---

### Post by darkmatter on 2005-10-15
That server has been taken off line (quie some time ago). For hoary-extras change the url to [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)

---

### Post by tay on 2005-10-15
!

---

### Post by tay on 2005-10-15
[http://ubuntu-backports.mirrormax.net/dists/sarge/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/sarge/main/binary-i386/Packages.gz:) 404 Not Found

i think it might be the /sarge/main

these were the default names given by the synaptic manager's repsitoriy editing window for the repsositories..  "directories??"  

what should i have typed there.

[ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz:) Unable to fetch file, server said 'Can't open /debian-marillat/dists/stable/main/binary-i386/Packages.gz: No such file or directory  ' [IP: 62.4.17.14 21]

---

