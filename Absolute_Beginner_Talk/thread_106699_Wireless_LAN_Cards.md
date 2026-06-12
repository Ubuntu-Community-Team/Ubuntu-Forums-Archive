---
title: "Wireless LAN Cards"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by KeithBurrage on 2005-12-21
Can anyone put me on to a driver source for wireless LAN Cards in particular
Edimax EW-7106PC or Linksys WPC54G? Some guidance on installation would also be welcome. The forum looks great, keep up the good work!:D

---

### Post by nijinsky on 2005-12-21
[QUOTE=KeithBurrage]Can anyone put me on to a driver source for wireless LAN Cards in particular
Edimax EW-7106PC or Linksys WPC54G? Some guidance on installation would also be welcome. The forum looks great, keep up the good work!:D[/QUOTE]

Hi Keith

Have a look at my attempts to get online in a Uni with the belkin card.
[http://www.ubuntuforums.org/showthread.php?t=99730](http://www.ubuntuforums.org/showthread.php?t=99730)

The link that got me sorted is perfect and I'm sure it can be addapted to your card.

All the best
Bob

---

### Post by Gamabunta on 2005-12-23
For WPC54G:

1. Install ndiswrapper-utils and ndisgtk (from universe) in synaptic
2. Make sure you get a new menu item - system>admin>Windows Wireless Drivers
3. Put in your card
4. Put in the wireless card driver installation CD
5. Goto Drivers>NT and copy the .inf file to your home folder
6. Open Windows Wireless Drivers
7. Install the .inf file, then configure your network
8. A new wireless option should appear
9. Enter in your wireless settings via 'properties'
10. Activate the card, restart, enjoy

---

