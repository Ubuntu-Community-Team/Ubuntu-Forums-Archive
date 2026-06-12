---
title: "What should I tick in Firestarter firewall to allow a local network to work."
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-12-28
I believe the Firestarter Firewall in Ubuntu may be preventing me from setting up a local network between two home computers connected via ethernet cables.  

On closer inspection of the Firestarter Firewall I see there are several items which may need to be ticked for local networking to function correctly. Woulds someone be kind enought to run me through all the items I should tick to ensure this happens please. I'd like to share files and a printer. My internet connection between both computers already works.

---

### Post by skymera on 2007-12-28
im not wsure about networking but anyway


open up firestarter and go to preferences.

in one of the tabs should be

Share Network and you canconfigure DHCP etc.
i tried to create network before and i failed.
so not much help,

Good luck

---

### Post by eolson on 2007-12-28
Edit Preferences and take your pick.   Ethernet is quick and easy.

---

### Post by Anduu on 2007-12-28
You can easily confirm if the firewall is the problem...

Start up Firestarter and and open the "Events" tab.If the firewall is blocking access,the ip of the other pc should come up in the window.***If*** that is the case it is as simple as right clicking the entry and selecting allow connections from source.

---

