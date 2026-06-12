---
title: "How can I install RAID on Gutsy?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by pmartiz on 2007-12-24
Before anyone starts, I am new to Ubuntu and now my boss wants me to install RAID on a server.  The problem is the server is an assembled leftover from former management.  I installed two 160GB hard drives and I am trying to create 4 RAID partitions on each and mirror them.  I vaguely remember doing this on Red Hat (eons ago) and thus, I am the 'expert' on doing this...hahahahaha!  I keep reading forums and posts on how to install RAID on Ubuntu 5.1 and it all seems to be command-line AFTER the installation.  Can anyone explain to me how to configure RAID _during_ the installation of Gutsy?

---

### Post by blueridgedog on 2007-12-24
Software RAID is a chicken and egg scenario.  If you want Ubuntu to setup the array, you have to have a non-raid partition for the kernel and other essentials to live.  Once the kernel and associated modules for software RAID are up and running, it can mount a RAID volume (that could hold your data or home directories).

A server should be configured for hardware raid if possible, failing that you can have a small boot drive with the OS and two larger drives that are setup for software RAID.

---

