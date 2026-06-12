---
title: "installing kbuntu"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by sports fan Matt on 2007-12-13
Hey guys.. I tried to install kubuntu but we had a flicker of power (installing cause it seems a bit lighter on my 382 memory celron processor) and now i get when i try synamptic  dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

How can i do this and erase what was downloaded and start from scratch?  or is it not that easy?

---

### Post by cyclefiend2000 on 2007-12-13
i got a similar error the other day. 

open a terminal window and type...
sudo dpkg --configure - a

pretty sure that is how i solved that. 

not sure about what you were downloading/installing.

---

### Post by sports fan Matt on 2007-12-13
hey cycle, thanks

Was trying to install kbuntu cause it feels lighter then ubuntu with my machine, but with the ice storm here in the midwest we have lost power alot and was just seeing if it was an easy fix or not..i'll give it a shot:)

---

### Post by sports fan Matt on 2007-12-13
this is the error i got while running that in the terminal..dpkg: error processing a (--configure):
 no package named `a' is installed, cannot configure

Any other ideas?

---

### Post by cyclefiend2000 on 2007-12-13
take a look at these...
[http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html](http://10xforce.blogspot.com/2007/09/dpkg-was-interrupted-you-must-manually.html)
[http://ubuntuforums.org/showthread.php?t=16233](http://ubuntuforums.org/showthread.php?t=16233)

hope that helps

---

### Post by DMK62 on 2007-12-13
Hi

When you run the command from the terminal ( Konsole ) make sure that you enter the command exactly. You may have missed the - before the a.

The command is:

sudo dpkg --configure -a

It may take a while to complete so be patient.

Having gone through countless ice storms up here in Canada you may want to give it a day or two before the power is stable. Besides unexpected shutdowns it isn't the best for the electronics.

HTH

Dale

---

### Post by sports fan Matt on 2007-12-13
Cycle, Thanks again...it seems to be reinstitating the packers that were broken...It seems that kubuntu will work better for me since im not running 512 ram, only 382...I'll keep u posted:)

---

