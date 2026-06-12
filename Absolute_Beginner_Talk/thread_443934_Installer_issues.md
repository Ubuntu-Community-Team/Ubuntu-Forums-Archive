---
title: "Installer issues"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by AWerner32 on 2007-05-14
whenever i try to run an installer of any type be it synaptic automatix or system update i am greeted with a lovely error . this is the one from synaptic

E: Dynamic MMap ran out of room
E: Error occurred while processing xfonts-cronyx-isocyr-misc (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by chili555 on 2007-05-15
This is a Debian oriented HOWTO that may help. Ubuntu is largely based on Debian. [http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

Especially read this:> You may find that you receive an error like the following:

E: Dynamic MMap ran out of room
E: Error occured while processing sqlrelay-sqlite (NewPackage)
E: Problem with MergeList /var/lib/apt/lists/ftp.us.debian.org_debian_dists_woody_contrib_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

This is caused because apt's cache is too small to handle all of the packages that are included with stable, testing, and unstable. This is also very easy to fix. Add the following line to /etc/apt/apt.conf

APT::Cache-Limit "8388608";
Since we do not have apt.conf, please try adding it to /etc/apt/apt.conf.d/70debconf with sudo gedit or sudo kate or, if you have a grey beard, sudo vim. The semi-colon at the end is important.

---

