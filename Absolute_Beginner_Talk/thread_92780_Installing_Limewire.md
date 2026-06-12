---
title: "Installing Limewire"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by nierz on 2005-11-20
Okay, I am new to Ubuntu Linux, or any other Linux for that matter, and I am just learning how all of these install features work, I am trying to install Limewire, so I did that, and then it said I needed Java, so when I Tried to install that. I typed this in the terminal:

> sudo apt-get install sun-j2re1.5
java -version

And I get this:

> Reading package lists... Done
Building dependency tree... Done
Package sun-j2re1.5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package sun-j2re1.5 has no installation candidate


I dunno what that means but could someone please help me.

---

### Post by zhorty on 2005-11-20
try
sudo apt-get install java-common

---

### Post by nierz on 2005-11-20
When I do that it says this:

> Reading package lists... Done
Building dependency tree... Done
java-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Is that good or bad?

---

### Post by UbuntuStudent on 2005-11-20
If you have been following the ubuntuguide, did you run "sudo apt-get update"?

If you havnt added repositories:

Open:
System>Administration>Synaptic Package Manager

Then go to:
Settings>Repositories

Then click ADD and check all
They should be there...

---

