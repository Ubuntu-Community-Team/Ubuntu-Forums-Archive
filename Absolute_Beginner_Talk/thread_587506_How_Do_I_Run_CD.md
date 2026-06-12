---
title: "How Do I Run CD?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by jdunk90 on 2007-10-22
I've got Ubuntu 7.10 on my computer.  Everything works fine, but I don't know how to run a CD like you normally would with Windows when you click on it.  When I click on the disc it breaks it down, but I've clicked on everything and I get an error on anything that isn't a text document.

---

### Post by barkej on 2007-10-22
What kind of items are giving you errors and what is the error that you are getting?

---

### Post by adamorjames on 2007-10-22
Can you be more specific? What do you mean by "breaks it down"?

---

### Post by TadH on 2007-10-22
i think he means it opens up the subfolderson the disc or something. what kind of cd are you rying to run?

---

### Post by click4851 on 2007-10-22
define "run" .....and I mean that in the nicest way. What are trying to make the files do? Cuz right off the bat I have to tell you .exe files are gonna be a problem. Your copy and paste functions should be okay, I guess it depends on the files themselves and what your default preferences are.

---

### Post by jdunk90 on 2007-10-22
I'm trying to start up the CD that goes with my graphics cards so I can get everything set.  Instead of just running it (for example if you click on the icon to play a game in windows) it just shows all the subfolders on the CD.

---

### Post by Maestro23 on 2007-10-22
> **jdunk90 said:**
> I'm trying to start up the CD that goes with my graphics cards so I can get everything set.  Instead of just running it (for example if you click on the icon to play a game in windows) it just shows all the subfolders on the CD.

Unless the software on the CD is for Linux, then those files are not going to work.  Are you trying to install drivers for you card?  If so, what type of video card do you have.

---

### Post by TadH on 2007-10-22
what kind of graphic card do you have.

---

### Post by jdunk90 on 2007-10-22
Leadtek GeForce 8400 GS.  What am I going to be able to do with Linux?  Will I be able to play any games while using it?

---

### Post by Maestro23 on 2007-10-22
> **jdunk90 said:**
> Leadtek GeForce 8400 GS.  What am I going to be able to do with Linux?  Will I be able to play any games while using it?

Your Windows games can be run under lInux in the following ways:

1. Thru a program called Wine.

2. Cedega

3. Run a Windows OS virtually.

4. Dual-Boot Ubuntu and XP/Vista

Wine: [http://www.winehq.org/](http://www.winehq.org/)

Cedega: [http://www.transgaming.com/](http://www.transgaming.com/)

*I'm a heavy gamer myself, it is the only reason XP is still on my system.

---

### Post by jdunk90 on 2007-10-22
Which is superior, Wine or Cedaga?

---

### Post by nchase on 2007-10-22
jdunk90 -- installing some solid nvidia drivers is as simple as going to main menu > administration > restricted drivers manager and enabling the nvidia drivers -- no need for that driver cd.

yes, many games run well on ubuntu. i can play valve's source games (like team fortress 2, day of defeat source, half life 2) adequately on a geforce 6600gt. also, many people report world of warcraft running flawlessly or near flawlessly.

---

### Post by nchase on 2007-10-22
i've only used wine and it's perfect for me. the one time i tried cedega it was horrible. it may have improved since then, but definitely try the free software option first.

---

### Post by jdunk90 on 2007-10-22
I'm a complete newb with all this technical computer stuff.  The wine site says input this for the new Ubuntu:   sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

What does that mean?

---

### Post by adamorjames on 2007-10-22
> **jdunk90 said:**
> I'm a complete newb with all this technical computer stuff.  The wine site says input this for the new Ubuntu:   sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

What does that mean?

It adds the new Wine to your list OR SO I THINK. So all you have to do is open Synaptic Package Manager and get it once you put that command into the terminal.. :)

Terminal is in Applications > Accessories
Synaptic Package Manager is in System > Administration

---

### Post by nchase on 2007-10-22
> **jdunk90 said:**
> I'm a complete newb with all this technical computer stuff.  The wine site says input this for the new Ubuntu:   sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

What does that mean?

it means literally input that line of text on the command line. copy and paste that line into a terminal.

---

