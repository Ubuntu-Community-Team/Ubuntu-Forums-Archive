---
title: "Synaptic Stuck"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by differential33 on 2007-06-01
Hi

I am using dapper and synaptic sems to have got stuck downloading Macromedia Flash.  When I go into Synaptic I get:

The following problems were found on your system:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

When I do this i get a dialogue box called "configuring flash -plugin nonfree" which asks me whether I want the flash plugin downloaded and installed with yes and no options at the bottom.

Clicking these produces no result.

while Synaptic is stuck, i can't install updates.  

How do clear this problem?

thanks
Russell

---

### Post by Outrunner on 2007-06-01
```
sudo dpkg --configure -a
```

And you don't click 'yes' or' no', you type either 'yes' or 'no' and press enter...

---

