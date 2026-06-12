---
title: "WiFi help needed"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by bbox9 on 2007-07-15
I've Kubuntu 7.0.4 installed and have not been able to properly setup WiFi, using a Trendnet 503pi pci card.

I'm completely new to Linux, and new to command lines.  Each google result offering help seems different from the last, and adds to my confusion.  

I've downloaded ndiswrapper and ndisgtk and have tried unsuccessfully to install and apply each. No doubt I'm doing something incorrectly, but at this point I have no idea what that might be.

Out of the box the KNetworkmanager stops at 28% config progress. 

Is it easier to set up WiFi with Ubuntu vs Kubuntu?

Any assistance would be much appreciated.

---

### Post by bbox9 on 2007-07-15
I've Kubuntu 7.0.4 installed and have not been able to properly setup WiFi, using a Trendnet 503pi pci card.

I'm completely new to Linux, and new to command lines.  Each google result offering help seems different from the last, and adds to my confusion.  

I've downloaded ndiswrapper and ndisgtk and have tried unsuccessfully to install and apply each. No doubt I'm doing something incorrectly, but at this point I have no idea what that might be.

Out of the box the KNetworkmanager stops at 28% config progress. 

Is it easier to set up WiFi with Ubuntu vs Kubuntu?

Any assistance would be much appreciated.

---

### Post by Happy_Man on 2007-07-15
Well, if you have been following a guide, could you post it here? That way, one of us can explain the steps better than a static guide could.

---

### Post by rohan000 on 2007-07-15
Maybe you can try installing Gnome via the ubuntu-desktop package. 
I haven't used Kubuntu but in Ubuntu wireless setup was really easy for me. The network manager applet that starts by default  detects wireless networks automatically.

---

### Post by tpg on 2007-07-15
> **rohan000 said:**
> Maybe you can try installing Gnome via the ubuntu-desktop package. 
I haven't used Kubuntu but in Ubuntu wireless setup was really easy for me. The network manager applet that starts by default  detects wireless networks automatically.
The underlying network manager is identical for Ubuntu and Kubuntu. If it doesn't work in KDE, chances are it won't in Gnome either.

The Trendnet 503pi should work fine out of the box - do you have any kind of wireless encryption (e.g. WEP or WPA) in use? Either that isn't set up properly, or the signal is not strong enough to make a connection.

EDIT: I should have mentioned - the fact that you can get to 28% configured means that Kubuntu can at least see your card (and available wireless networks), so that means there probably isn't a driver problem.

---

### Post by bbox9 on 2007-07-15
Eureka! 

After playing with the pci card antenna orientation on the desktop the WiFi connection now works! 
With so many other possibilities, I overlooked this one. 

As suggested, that might explain the 28% configuration progress experienced earlier. The received signal was too weak.

Many thanks for your help.

---

