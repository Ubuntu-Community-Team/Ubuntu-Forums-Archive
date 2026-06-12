---
title: "HP deskjet D2460"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by Radical62 on 2008-02-18
well as the thread states i have a deskjet D2460 and i cant get it to work under ubuntu.  i have installed all the hp drivers in the synaptics package manager, but whenever i try to print, it loads for a few seconds and then says "Error while printing"

Anybody have any ideas?

---

### Post by bumanie on 2008-02-18
Go to this HP site [http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)
Download the self-extracting archive with installer to your desktop. Open terminal command > cd ~/Desktop --> enter theen command > sh hplip-2.8.2.run , answer a few questions and the installer should do the rest, including installing all dependencies.

---

### Post by Radical62 on 2008-02-18
installer worked fine, i rebooted, same problem is occurring.

i noticed that when i click print in openoffice word, the printer that comes up is "Generic Printer".  is this just because linux cant read what printer this is, or should it say "HP Deskjet D2460" like on windows?

---

### Post by Radical62 on 2008-02-18
problem solved, all i had to do was use the new printer wizard :P

---

### Post by fatality_uk on 2008-02-18
> **Radical62 said:**
> problem solved, all i had to do was use the new printer wizard :P

Glad it worked :D

Can you mark the thread as solved please ;)
Cheers

---

