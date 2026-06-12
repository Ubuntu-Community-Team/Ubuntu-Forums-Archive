---
title: "Problem upgrading from Kubunto 6.10 to 7.04"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Shadowgaze on 2008-01-02
I'm trying to upgrade from 6.10 to 7.04 in an attempt to get Wine 0.9.6 to run so I can run WoW.  The problem I'm having is I keep hitting a wall while I run the upgrade.   All the packages upload fine, but during the installation process a screen comes up for me to 'Configure MDADM.  It has to do with starting the MD array.  It gives me the option of what I want to start or to start all or none, but theres no place that I can enter the selection I made.    This happens right at the beginning of the install portion of the upgrade.I am unable to get any farther then this as i will not let me progress past this step until I make a selection.

If I try to run the updates individually I get the fallowing fault.

E: /var/cache/apt/archives/xserver-xorg_1%3a7.2-0ubuntu11_all.deb: subprocess new pre-removal script returned error exit status 1

---

### Post by Xzallion on 2008-01-04
What are you doing to upgrade?  Using update manager, synaptic, or apt-get?  If you haven't, try running ```
sudo apt-get dist-upgrade
``` from the terminal.

---

