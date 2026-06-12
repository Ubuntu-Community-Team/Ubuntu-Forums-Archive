---
title: "synaptic error"
date: 2005-12-23
forum: Absolute Beginner Talk
---

### Post by Colenzo on 2005-12-23
When I use synaptic I get the error below.

I think It's because I changed a code in terminal... please help!


W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


Oh ya, this may be off topic but can someone give me some detailed instructions on getting an app that will burn cds??? Mucho thnx

---

### Post by jbmalone on 2005-12-23
Get Gnomebaker, it's the best burning program I have found so far.

---

### Post by akniss on 2005-12-23
Try clicking the Reload button in the top left corner of synaptic, see if that fixes your errors.

---

### Post by KEMitchell on 2005-12-23
This is a message passed up through Synaptic from the console program "apt-get" which handles packaging on Debian linux boxes and derivative distros (e.g. Ubuntu).

Basically it's telling you that it can't get a hold of the files on those servers (as listed in your /etc/apt/sources.list file) that give apt-get information about available packages, etc.

Check to make sure that the addresses are correct, that the repositories (e.g. package hosting sites) at those URLS still exist, and that you are able to connect to those servers with your internet connection.

---

### Post by TeeAhr1 on 2005-12-23
Questions:
1. What version of Ubuntu are you using?  I noticed that it's looking for Hoary backports.
2. What file did you edit and what did you change?
3. Did this start immediately afterward, or later?

---

