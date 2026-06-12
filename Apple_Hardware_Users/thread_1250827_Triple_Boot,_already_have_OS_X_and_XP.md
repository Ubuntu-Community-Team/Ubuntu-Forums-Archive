---
title: "Triple Boot, already have OS X and XP"
date: 2009-08-27
forum: Apple Hardware Users
---

### Post by carlosjoan91 on 2009-08-27
Hi, I have a macbook, (black, the last ones before the switch to aluminium, I think it's santa rosa), and have OS X, and installed Windows XP using boot camp, I want to add a Ubuntu partition, have installed and used ubuntu for a long time before, but on my Desktop (non apple) computer, so I just want to know, can I just install Ubuntu as I would on a non-mac computer(i.e. use the ubuntu disc to partition and install)? I have read plenty of how-to's, but I still don't understand if rEFIt is neccesary or if I can use the normal mac boot program, if I do need EFI, can I install it and then install ubuntu normally?, if this process(Installing Ubuntu when you already have OS X and XP installed) is documented anywhere, please give me a link, I couldn't find anything, thanks!

Sorry for all the questions, but I couldn't find anything that talked about this specific situation (installing ubuntu last)

---

### Post by beastrace91 on 2009-08-27
You should be able to install Ubuntu Last with out any issue, just have it resize the drive as normal. I've never personally multi booted an OSX system but Ubuntu should auto create an entry for it in the grub menu (along with an entry for Xp).

And on the off chance it doesn't auto create the entry it is as simple as adding ```
title Mac OSX Leopard
rootnoverify (hd?,?) (replace ? with the values Grub uses for OSX partition)
chainloader (hd?,?)+1 (same values)
``` to your /boot/grub/menu.lst

~Jeff

---

