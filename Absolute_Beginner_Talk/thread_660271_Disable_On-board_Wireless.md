---
title: "Disable On-board Wireless?"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2008-01-06
I just got a new PCMCIA wireless card in the mail (one that works by default with Linux).  How do I disable my on-board RTL8185 and install the new one?  

Thanks, love Ubuntu!

---

### Post by philinux on 2008-01-06
I think you'll have to go into the bios to sort it out.

---

### Post by brandoncolorado on 2008-01-06
I went into my bios and couldn't find anything related to my wireless card.

I did this already to:

sudo gedit /etc/modprobe.d/blacklist

and added:

# disable RTL8185 for new wireless card
blacklist rtl818x
blacklist rtl8180
blacklist rtl8185
blacklist r818x
blacklist r8185

However, the rtl8180 driver is still shown as loading.

What gives?

---

### Post by philinux on 2008-01-06
I'm pretty sure it's in the bios under the advanced tab.

Look for embedded wireless then disable it.

Or maybe there a switch on the laptop itself

---

