---
title: "Re-enabling GDM?"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by FluffyLogic on 2007-07-24
I've modified a setting somewhere -- I thought I was just turning off services -- bluetooth and the HP printers, but I have also seemed to have stopped something in GDM

When I log in, I am not presented with a login screen, but instead get a dialog that scans for running hosts.I'm just trying to connect to the local computer I click cancel, which brings me back to the initialization messages, but I cannot log in. Can someone please tell me how I re-enable GDM to work correctly so I can log into my own computer? I can start recovery mode, and can log in a root, so I can fix the problem, I just don't know how.

Any help would be most appreciated.:confused:

---

### Post by Sbarton on 2007-07-24
If you have access to terminal maybe this will help

sudo apt-get install &#8211;reinstall xserver-xorg
sudo apt-get install &#8211;reinstall gdm
regards

---

