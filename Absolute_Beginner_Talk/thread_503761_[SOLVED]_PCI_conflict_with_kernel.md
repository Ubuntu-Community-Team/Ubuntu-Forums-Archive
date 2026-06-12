---
title: "[SOLVED] PCI conflict with kernel?"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-07-18
Feisty, running on a Dell Dimension 4100. 

Synaptic has installed everything madwifi.

I put the d-link wda 2330 card into the pci bus.

lspci shows no such card 

adding line to grub; pci=assign-busses

causes x server to fail on boot

I have tried 2 pci slots.

What boot log file(s) show evidence of pci details?

---

### Post by Mark_in_Hollywood on 2007-07-20
The card itself was bad. it has been replaced and the output of lspci shows it on the bus. thank you.

---

