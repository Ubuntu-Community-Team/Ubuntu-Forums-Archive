---
title: "Errors on imac g3"
date: 2007-04-27
forum: Apple PPC Users
---

### Post by Drex89 on 2007-04-27
So, when i start Ubuntu, I get 8 error messages. Seven of them say, "The panel encountered a problem while loading OAFIID:GNOME_(NotificationAreaApplet, ClockApplet, TrashApplet, ShowDesktopApplet, MixerApplet, WorkspaceSwitcherApplet, or WindowListApplet). The other one says, "Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting nautilus may help fix this problem." When I type "killall bonobo-activation-server", it says "No process killed." I'm fairly new to Ubuntu, but this just started happening recently. Any suggestions as to what I should do?

---

### Post by marcthenarc on 2007-04-29
I don't know if this would help, but the first time I had this error was when I tried to start a graphical install of Ubuntu on a iBook G3 with 128 mb of memory.  The low memory and constant swapping between disk and ramdisk must have killed my application expecting a faster response.  After a text install, I could use it properly.  So if you already installed it on your iMac, is it low memory ? maybe swap settings ? hd parameters ?

If someone has a better solution, feel free to add.

---

### Post by Drex89 on 2007-04-29
Unfortunately, I did use the text based alternate cd. It worked for a while, but now it doesn't anymore.

---

### Post by suzukix on 2007-06-30
I am having the same exact errors on a Powerbook G4 after Ubuntu has worked for days. One morning it booted with these errors. Have you come across a solution?

Thanks.

---

### Post by trobn76 on 2007-11-30
I have a similar iMac, and am having the same difficulty -- I have posted the error messages in a thread in detail [here]("http://ubuntuforums.org/showthread.php?t=628165")

---

### Post by DirtDawg on 2007-12-01
I believe you all may have a dead PRAM battery. The computer cannot load the applications because your computer thinks it's 1901(or something similar) and the apps haven't been invented yet (computers are stoopid).

If this is the problem, you need to set the hardware clock to the correct time. Please note that until you replace the PRAM battery, you will need to repeat this process any time the computer loses power or is unplugged (turning it off and on doesn't seem to cause a reset).

There are more detailed instructions [here]("http://ubuntuforums.org/showthread.php?t=244685&highlight=hwclock"). I hope this is of use. Good Luck.

---

