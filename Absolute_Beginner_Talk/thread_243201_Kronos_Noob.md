---
title: "Kronos Noob"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by kronos_black on 2006-08-24
Hey im fairly new to ubuntu but my dad isnt and he cant figure out whats wrong...i recently installed 3dDesktop switcher right and i have my shortcut key set up and all but it doesn't run so i tried to start it threw the terminal and it said:


Attempting to start 3ddesktop server.
Daemon started.  Run 3ddesk to activate.
3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

so i did i typed 3ddeskd and got this:


3ddeskd: glXIsDirect failed, no Direct Rendering possible!
3ddeskd: Please configure hardware acceleration.  Exiting.
Daemon started.  Run 3ddesk to activate.

so then i ran 3ddesk to activate it and got the same error and was told to try starting it manually but whenever i try it says something bout the glXIsDirect and it failing....what is it and why is it failing?

---

### Post by RadixLecti on 2006-08-24
My guess would be that your graphics card drivers aren't installed, or configured correctly.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

If you have an ATI card, follow the BinaryDriverHowto. I used the "Using the drivers from ati.com"-option. Worked like a charm.

If you're using Nvidia, you're in luck. Much easier. ;-)

---

### Post by kronos_black on 2006-08-25
ok thanks it worked perfectly
now how do i use 4 different desktop pictures instead of just one?

---

