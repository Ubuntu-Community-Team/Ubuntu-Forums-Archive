---
title: "Adding DVD to repository in Adept"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Xierxes on 2007-09-01
Hi all,

I have a question in regard to adding a DVD as a repository in Adept. I have just completed a clean install of Kubuntu Fiesty. I need to install ndiswrapper for my usb wifi dongle (Netgear WPN111) and although I have downloaded the packages I want to ensure I get the dependecies correct by using the package manager.

The problem that I am having is that when I try to add the DVD using sudo apt-cdrom add it is looking for the cd at /cdrom/ rather than the correct mount point. I have tried making a link but this does not work either. Any help would be appreciated,

Cheers

---

### Post by str8line on 2007-09-02
If the DVD is the installation DVD that you installed Ubuntu from, open Synaptec and enable the DVD from the Repositories menu.  The only problem with this is that every time you install software or updates it will request the DVD.

---

