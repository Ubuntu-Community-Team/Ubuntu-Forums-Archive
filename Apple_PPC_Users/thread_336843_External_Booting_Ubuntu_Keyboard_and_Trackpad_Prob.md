---
title: "External Booting Ubuntu Keyboard and Trackpad Problem"
date: 2007-01-12
forum: Apple PPC Users
---

### Post by neosx on 2007-01-12
I installed Ubuntu Server 6.10 to an external firewire hard drive on PowerBook G4 12''.

As usual, installer failed to install yaboot into bootstrap partition, therefore I installed it manually. I also installed a customized kernel in order to enable firewire capabilities on boot.

Although it was working during installation, my built-in keyboard does not work at all after boot. I encountered this problem with desktop 5.10, and probably 6.06, with same installation conditions. In those cases touchpad was not functional either, though a USB mouse was working properly.

Is there a problem with my custom kernel compilation? How can I solve the issue?

---

### Post by neosx on 2007-01-14
Problem is solved. Probably old config file did not include input related stuff, after using config file from live cd as base everything began to work properly.

---

