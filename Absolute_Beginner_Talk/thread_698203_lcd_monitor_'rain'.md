---
title: "lcd monitor 'rain'"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by ecs_pf5 on 2008-02-16
I'm using a 1680 x 1050 native resolution LCD monitor 'hp w2207'

I have an ATI Radeon x700 card, connected via the VGA connector.

I am using the fglrx driver. I had to make modifications to the system & xorg.conf to get it to work:

- remove 'quiet splash' from '/boot/grub/menu.lst' lines
- add Option "Composite" "Disable" in Section "Extensions" in xorg.conf
- add Option "AIGLX" "off" in Section "ServerFlags" in xorg.conf
- do sudo aticonfig --overlay-type=Xv
- added '1680x1050' to the top of all mode lines in xorg.conf to let me select that res in the gui app on the Gnome desktop

Now the problem; if I set the Desktop background to black, or a very dark colour, I get 45 degree 'rain'. It's just like looking out of a window into a rainstorm.

Anyone else seen this, is it a common problem, is it dangerous to the monitor.. ? It caught my attention a week or so ago as a 'shimmer' but it was only just now I really looked at it & saw that it was individual pixels sheeting across the screen at 45 degrees really fast, making hundreds of faint traces

Beginning to wonder whether I should throw this ATI card in the bin and go and get an nvidia one :confused:

---

### Post by natirips on 2008-02-16
This probably won't help, but there is a small possibility it helps: check you monitor cable. :)

Also you can check if your card is sitting properly in the AGP / PCIE slot, also it's power cable (the small one with four colored wires - two black, one yellow and one red) (if the card has one (I know x1600 has it)). And yes, DO NOT OPEN YOUR COMPUTER CHASIS IF IT WOULD BREAK WARRANTY OR YOU HAVE NO KNOWLEDGE OF HOW COMPUTER HARDWARE WORKS.

---

### Post by ecs_pf5 on 2008-02-16
Powered off & disconnected cable both ends. This was a new cable that came with the monitor a month or so ago. Seems undamaged visually.

Case is already open, it's a home-assembled machine so no guarantee to worry about. Removed card & reseated. There's no connector at all on the card for power, however the slot on the motherboard does have a normal 4-pin power socket right hard up against it. This has got a plug in it that goes back to the PSU. Unplugged it & replugged it. [edit] manual says this is 'ATX4PI (aux power for graphics cards)'

[edit] slot in which vid card inserted: 'PCI express x16 (PCIEX1)'

There was a ribbon cable on the vid card going from VGA socket to a header on the board, replugged it.

Reassembled everything, & rerouted VGA cable to avoid mains leads etc.

Rebooted, still got rain.

Thanks for the suggestions, worth a try eh.

---

### Post by natirips on 2008-02-17
I'm sorry but if that's the case, I am unable to help you... the only LCD I have at home is the one on my laptop...

---

