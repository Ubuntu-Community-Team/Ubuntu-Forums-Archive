---
title: "Gaming and Optimus Question"
date: 2011-11-07
forum: Asus Ubuntu Support (CLOSED)
---

### Post by kkozy on 2011-11-07
I am currently running Ubuntu on my Asus N53J without any issues. 

However, I would like to play some graphic intensive games through Wine. I have confirmation through WineHQ that the games I want to play have been successfully installed and run through Wine. 

Unfortunately I cannot play any games, even those not requiring 3D acceleration like Civ IV. The error I get suggests Wine is not detecting the Nvidia card. I have tried using several drivers and the use of Bumblebee and nothing is working. 

Can anyone help? I'd really hate to put Windows back on this machine, even using a dual boot. 

Note: All games are being installed from the original disk with no cracks or hacks.

---

### Post by AureiAnimus on 2011-11-07
You can try using bumblebee or iron hide ( [https://launchpad.net/~bumblebee](https://launchpad.net/~bumblebee) or [https://launchpad.net/~mj-casalogic/+archive/ironhide/](https://launchpad.net/~mj-casalogic/+archive/ironhide/) )

Bumblebee is more stable, but does not by default try to support powersaving and is maintained by a couple developers.
Ironhide is from the person who originally developed bumblebee and does not attempt to be perfectly stable but does provide powersaving configurations (including for your model)

if successful you should be able to run the games by typing this in a terminal:
```
optirun wine <program>.exe
```

Mind that this runs games through two layers, one for the graphics card and wine, so it's likely that some games don't work.

---

