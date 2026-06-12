---
title: "My ethernet port is gone"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Griffongob on 2006-12-28
While trying to get my wireless card to work with ubuntu my ehternet port suddenly is no longer recognized by both ubuntu and XP. Does anyone have ideas as to how i can fix this or if a clean install of windows and then ubuntu would fix this?

---

### Post by bernied on 2006-12-28
This sounds a bit hardware-ish to me. Are both cards PCI (internal)? Is it possible that you disturbed the wired card when installing the wireless card?

Things to try - 
- does the cad show up with lspci (maybe sudo lspci)
- does a live cd detect the card? (lspci again)
- does the card reappear if you remove the new wireless card?

Reinstalling both OSs sounds very drastic to me.

---

