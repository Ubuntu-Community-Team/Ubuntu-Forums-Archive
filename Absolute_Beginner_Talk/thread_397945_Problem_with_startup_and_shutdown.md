---
title: "Problem with startup and shutdown"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by andyni1 on 2007-03-31
Sorry if i have missed a thread on this problem.

Last night I installed 6.06 LTS as dual boot with XP pro on my new Fujitsu Siemens laptop. The first problem I noticed was that during start-up the boot screens appears about half of the computer screen. All becomes well again after the desktop is loaded but when I try and shutdown instead of a splash screen I am left with a black screen with random orange lines running horizontally through it and the machine freezes. Can anyone shed any light on the possible problem?

Thanks

Andrew

---

### Post by wpshooter on 2007-03-31
What brand/model of video card does the machine have ?

---

### Post by andyni1 on 2007-03-31
UniChrome Pro is the graphics card listed on the box.

---

### Post by nixclusive on 2007-03-31
It almost certainly is a problem with your video card. But before that, you can try turning off the splash screen and check wheather it fixes the problem.

In the initial GRUB menu, press 'e' on the menu entry that starts Ubuntu. Press 'down' to reach the line starting with 'kernel...'. Press 'e' to edit this line, scroll to the far right and remove the word 'splash'. Press enter, press 'b' to boot.

---

### Post by andyni1 on 2007-03-31
That fixes the startup problem, but how do I stop it from happening with the shutdown.

---

### Post by louieb on 2007-03-31
Have you done to 180+ file update that comes after a fresh install? The GParted live CD had a freeze on shutdown problem on certain computers, mine included. That problem was fixed with the last version of the GParted CD. 
Hope the fix is easy as updating  the PC.

---

