---
title: "ink levels"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by james99 on 2006-09-24
Question? how does 1 monitor the ink levels for the installed printer.
I print without a problem, but it would be helpful to know when a cartridge needs replacing.And no the thread I checked for epson didnt work 4 me.

---

### Post by nts on 2006-09-24
Have a look here:-

[http://www.linuxformat.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=4164](http://www.linuxformat.co.uk/modules.php?op=modload&name=PNphpBB2&file=viewtopic&t=4164)

---

### Post by ron999 on 2006-09-24
Hi james99
You need to install, using Synaptic, programs mtink and mtink-doc.
When they're installed you run the program from the terminal by typing 
sudo mtink
This program shows the ink levels and also cleans printer nozzles and aligns heads.
This program works for Epson printers, I don't know about any other makes.

---

### Post by petri on 2006-09-24
This was greate. Is there any possibility to make a starter with sudo involved to mtink?

---

### Post by ron999 on 2006-09-24
Hi petri
I don't know how to make a menu shortcut to mtink because it needs sudo rights.
Maybe someone else will come up with a solution.

---

### Post by xpod on 2006-09-24
Cheers folks.....something i had`nt even considered yet for this old epson sc 800....
Not that we use it much.....I make the kids WRITE their homework:twisted:

---

### Post by james99 on 2006-09-24
Thank you ron999, worked a treat.

---

