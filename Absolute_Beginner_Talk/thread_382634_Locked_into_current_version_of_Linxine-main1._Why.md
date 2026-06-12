---
title: "Locked into current version of Linxine-main1. Why ?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Sweet Spot on 2007-03-12
Whenever I use update manager, I get a message 
> Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely. And then libxine-main1 is skipped. If I do sudo apt-get get, it does nothing, and when I go into Synaptic and do "mark all upgrades", nothing appears. 

When I search for libxine main1, it has a lock icon over it, and says it's locked into version  2.7.6   What is holding it back from upgrading ?

Doug

---

### Post by ThrobbingBrain66 on 2007-03-12
> **Sweet Spot said:**
> Whenever I use update manager, I get a message 
 And then libxine-main1 is skipped. If I do sudo apt-get get, it does nothing, and when I go into Synaptic and do "mark all upgrades", nothing appears. 

When I search for libxine main1, it has a lock icon over it, and says it's locked into version  2.7.6   What is holding it back from upgrading ?

Doug

It's possible that you accidentally locked the package when doing something else.  To remedy this, search for the package in question and highlight it.  Then in the menu bar, navigate to Package and uncheck the 'lock package' check box.  This should allow you to upgrade libxine.

---

