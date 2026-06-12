---
title: "Help with wireless"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by drewhiggs on 2007-10-25
I am trying to see if my wireless card is recognized by ubuntu, but I do not know where to find this setting.  Everything I read says to go System\Administration\Networking.....but all I have is Network and Network Tools.  If I run network-admin, it says that I do not have permission, but I am the only user....?

Any advice?

---

### Post by Crafty Kisses on 2007-10-25
> **drewhiggs said:**
> I am trying to see if my wireless card is recognized by ubuntu, but I do not know where to find this setting.  Everything I read says to go System\Administration\Networking.....but all I have is Network and Network Tools.  If I run network-admin, it says that I do not have permission, but I am the only user....?

Any advice?

Before you run the  "network-work admin" command, try the following command:
```
sudo -i
```
That should make you root, then after that, it should work.

---

### Post by drewhiggs on 2007-10-25
Headway!  How do I enable the network now?  

When I type sudo lshw -C network....I get... *-network DISABLED....how do I enable this network.  When I select wireless properties....the only check I get is to enable roaming mode.  What should I do now?

Thanks for your help

---

### Post by plinydogg on 2007-10-25
Wait for feedback from more experienced minds (I'm a newbie!) but I had problems getting my wireless to work too. 

(1) First thing I did was enable the restricted driver for my wireless card (system->admin->restricted drivers manager); and then 

(2) Installed a program called WICD (it's available from the Synaptic Package Manager) and it immediately detected my card.

Again, don't do this until someone else weighs in. 

BTW, what kind of wireless card is it?

---

### Post by drewhiggs on 2007-10-25
I have a dell wireless 1390 WLAN Mini-PCI card (weird, I have an HP laptop)....that is what shows up when I type sudo lshw -C network.

I may go ahead and try your suggestion.  Thanks for the input

---

### Post by drewhiggs on 2007-10-25
It says that my hardware doesn't need any restricted drivers:confused:

---

### Post by plinydogg on 2007-10-25
Well, WICD may still work for you, but as I said, I suggest you wait until someone more knowledgeable chimes in.

Installing WICD will uninstall the default Network Manager and so you may put yourself in a worse position if it doesn't work.

Good luck....It's time for me to get some sleep...

---

