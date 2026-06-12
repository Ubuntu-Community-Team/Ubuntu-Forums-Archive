---
title: "Which Graphics Card is being used? 9600M or 9600mGT?"
date: 2009-07-25
forum: Apple Hardware Users
---

### Post by fosheezy on 2009-07-25
I've got a July 09 macbook pro, with the 9600m and the 9600m GT 512MB.  How do I know which one ubuntu is using? Can I switch between the two?

I feel like it is using the integrated card instead of the dedicated card, beacuse I've got 64bit 9.04 installed and it only shows 3.7 GB ram available, when i've got 4. This makes me think the integrated card is sharing memory.

---

### Post by 67GTA on 2009-07-25
Open a terminal and run ```
lspci
``` This will give you a short list of PCI devices and there names. You can get a lot more info with ```
lspci -vnn
``` and the drivers being used for said devices. I would guess that the card not being used won't show any driver info.

---

