---
title: "graphics problem when installing"
date: 2008-02-18
forum: Absolute Beginner Talk
---

### Post by stormtrooprdave on 2008-02-18
im trying to run the livecd to check out ubuntu but having problems.  I choose start or install ubuntu from the option screen, then it runs for a while doing the various components (white text on black screen with ok at the side of each item) then when all that has done ( i think) instead of seeing the live desktop screen all i get is a light brown screen with a big white block for a mouse cursor and nothing else.  There is  some graphical glitches as well (sorry cant get pics to show)

i have dual core pc pentium d 2.8ghz, 2gb ram, 250gb hdd, nvidia 7950gt oc, windows xp sp2

im trying to have a play with ubuntu to see if its worth installing as a dual boot but cant get it to display properly and looking through the forum here no one seems to have the same problem

---

### Post by kaiju on 2008-02-18
have you tried booting the cd in safe graphics mode (second line of the boot screen, i think) or using different vga settings (F4 when the boot screen shows up)?

---

### Post by stormtrooprdave on 2008-02-19
yes tried it in safe graphics mode and on different resolutions, nothing seems to have an effect and i get this brown screen everytime i try.  im about to give up on it really, if installing the OS is screwed up it doesnt give me high hopes for teh rest of it

---

### Post by hopelessone on 2008-02-19
i have nvdia and installed something called ENVY !!!

problem solved!!

---

### Post by stormtrooprdave on 2008-02-19
had a quick look at envy and i think i would need to install that from the ubuntu desktop, but i cant get to the desktop at all because all i get is the brown screen and the big white block square for the cursor

---

### Post by Fred_E _krugar on 2008-02-19
Make sure the MD5check some is correct. You could check CD on the Ubuntu Splash screen.

---

### Post by uberlube on 2008-02-19
When you are in the CD boot menu, press F6 while 'Run or install Ubuntu' is highlighted and manually enter 'irqpoll vga=791' and press enter. Worked for me:)

---

### Post by stormtrooprdave on 2008-02-20
i checked the iso and did the memory check from the instalation menu so no problems with the disc

i tried that irqpoll vga=791 and it didnt work, nothing came up at all, although funnily enough the first time i tried it i mistyped irqpoll vg=791 and i did actually see the menu bar at the top of the screen, although it was still heavily corrupted and unusable

think ill wait for the next release, hope it works better than this one

---

