---
title: "Nothing loading - Exiting PXE rom"
date: 2008-01-07
forum: Absolute Beginner Talk
---

### Post by LouisChappell on 2008-01-07
I was on the train today watching a film adn the battery came loose, when i turned it back on i got a message saying 
> Intel UNDI, PXE-2.0.........
Copyright......
For Realtek ...... PCI Ethernet Controller...
PXE-E61: media test failure, check cable
 PXE-M0F : exiting PXE ROM

I understand it to be  a bios problem, i have a compaq latop. I'm at a loose and and DESPERATELY need my laptop this week for revision purposes exams=a bigger nightmare.

thanks in advance for any help!

---

### Post by stump138 on 2008-01-07
this means that you are trying to boot off of your network card and you don't have it plugged into a network with PXE services (used for imaging and thin clients) when you start your computer.  You can turn off network booting in your bios.  You should only need to alter your boot order and make sure the hard disk is tried before the network card.

---

### Post by LouisChappell on 2008-01-07
Cheers for the reply, now I just get a flickering Operating System not found. Does this mean it's game over? I have a lot of important uni work on both ubuntu and xp partitions is it all lost?

---

### Post by stump138 on 2008-01-07
if you have it set booting off of the hard disk and you are getting that message, it's generally not a good thing.  Boot off of a live cd and try to remove as many of your important files as possible to a USB drive before you attempt to fix on that issue

---

### Post by LouisChappell on 2008-01-07
I don't think it could get that far, it seems to think there's no disk drive present which would explain why it was booting in such a way.
not sure if i have the right live install disc either as it has no option to do so.
thanks for the additional help

i've tried to search for more  help but can't seem to find any existing pages on it could someone point me to a relevant place?

---

### Post by LouisChappell on 2008-01-08
so i take it there's nothing i can do?
i'd need to get a new HDD?

EDIT: HDD was dead sent off and replaced thanks for the help anyway.

---

