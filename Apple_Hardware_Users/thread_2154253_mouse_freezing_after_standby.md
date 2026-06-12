---
title: "mouse freezing after standby"
date: 2013-06-14
forum: Apple Hardware Users
---

### Post by Heliophon on 2013-06-14
Hi,
I am using a PowerBook G4 1,67 15" with Lubuntu 13.04: All updates are done regular with SoftwareUpdater.
My problem is: after wake up from standby mode the mouse is freezed and I must restart Lubuntu.
Searching the forum did not reveal a solution.
Any ideas?
Best wishes from Germany,
Heliopphon

---

### Post by este.el.paz on 2013-06-15
> **Heliophon said:**
> Hi,
I am using a PowerBook G4 1,67 15" with Lubuntu 13.04: All updates are done regular with SoftwareUpdater.
My problem is: after wake up from standby mode the mouse is freezed and I must restart Lubuntu.
Searching the forum did not reveal a solution.
Any ideas?
Best wishes from Germany,
Heliopphon

@Helio:

First thing to mention is that from what people who know Linux have told me over the last couple of years is to **Not*** use SoftwareUpdater to do updates; either use the Terminal with ```
sudo update
``` and then ```
sudo upgrade
``` or in some cases ```
sudo dist-upgrade
``` . . . and then enter your password and let the Terminal Aptitude run the upgrades.  Or, use Synaptic packagae manager to install packages . . . this is what I've been told, and I'm just a GUI user.

In terms of the "freezing mouse" . . . usually these kind of issues are due to not having the right xorg.conf file for your computer; check the PPC FAQ and see if you find anything there about the mouse freezing or how to get the right xorg.conf file.

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

e.e.p.

---

