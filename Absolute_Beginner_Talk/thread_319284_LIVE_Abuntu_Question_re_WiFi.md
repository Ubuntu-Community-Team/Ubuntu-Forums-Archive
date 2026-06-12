---
title: "LIVE Abuntu Question re WiFi"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by lawrencrj on 2006-12-15
I have the older version of Ubuntu and am running it from a CD.
My WiFi works fine on XP but NOT on Ubuntu.
I have looked for a fix in the BIOS as someone suggested and found no fix.

QUESTION:
Has anyone at all had their WiFi work when running Ubuntu from the CD??

---

### Post by saxsux on 2006-12-15
It's probably not a problem with your wireless card, more likely to be that Ubuntu doesn't recognise your wireless card.

Do you have the Windows versions of the drivers available? If you can, you should be able to get your card working using something called ndiswrapper.

---

### Post by Kobalt on 2006-12-15
You can get your Wifi card to work with the LiveCD, but Wifi cards most of the times require configuration before working. It depends on what car you have actually ? 
If you don't know precisely, type this command line, it will give you hardware information : 
```
lspci
```

---

