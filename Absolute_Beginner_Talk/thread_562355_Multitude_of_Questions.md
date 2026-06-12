---
title: "Multitude of Questions"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Elycian on 2007-09-28
Soooo I recently installed Ubuntu Fiesty, I'm having a lot of problems though

- I have to paste "compiz -replace" in the terminal everytime I reboot to allow compiz-fusion to work.. Any way to fix this?
- Second the sound randomly leaves when I come back from rebooting and then comes back on other boots..
- And third though not important, is there any recommended websites for downloading themes for ubuntu?

Thanks :]

---

### Post by loserboy on 2007-09-28
sorry i can only answer one question  [www.gnome-look.org](www.gnome-look.org) or [www.kde-look.org](www.kde-look.org) (for gnome or kde respectively)

---

### Post by Vixis on 2007-09-28
1)System -> Preferences -> Sessions
Startup Programs -> New, paste ```
compiz -replace 
```in command.

3) Try [gnome-look.org]("http://http://www.gnome-look.org/")

---

### Post by wormser on 2007-09-28
1.  Go to System> Preferences> Sessions> Startup Programs tab.  Click New and put "compiz -replace" in.

2.  I am not sure what the problem is.  Does the sound only not come back on reboots?  Does a cold boot make the sound work?  It would be good to find out what hardware you have.  Post the model number of your sound card from the command lspci.

3.  Try [http://www.gnome-look.org/](http://www.gnome-look.org/)

---

