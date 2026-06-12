---
title: "network issues upgrading from 6.10-7.04"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ITdrummer on 2007-06-13
Ok, I successfully installed ubuntu version 6.10 without a hitch.  I am now attempting to upgrade to the current Feisty release.  I go to the update manager in the GUI and i see that the update is available. I click on "upgrade" and it prompts me for a password. I input my password, then it acts like its going to begin the download then an error message pops up.  "Network authentication failed."  I would assumer that it was my network card driver that wasnt jiving right with the OS, but i can get on the internet no prob.......puzzling

---

### Post by jhenager on 2007-06-13
First thing I do when I get any kind of network error is look at the network icon in the taskbar to see if there is a  little red mark next to it. If all you see is two monitors, you should be good.
To doublecheck, open up a terminal and type 'ifconfig' and hit enter. If you see 
inet addr: 192.168.1.x (or 172.16.1.x or your usual IP address)
you should be good, and I would just check to see if you are using the right password.

---

### Post by nfs510 on 2007-06-13
I have the same problem and found some ans from:

[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html]("http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html")


but it did not help me, maybe I did something wrong. Perhaps you have better luck.

---

