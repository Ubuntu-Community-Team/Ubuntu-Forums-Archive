---
title: "Edgy won't shut down"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by 1972_OLDS_442 on 2007-05-06
Help, Everything in Edgy works except shutdown!?:confused:  When I go to shutdown I click on the button and everything closes out then the splash screen comes up with the bar that shrinks. It gets down to nothing in the bar and just stays there, I have left it running thinking it just takes a while, but 15 min later it's still on the screen.

Does anybody have any suggestions?

---

### Post by bobplano on 2007-05-06
try ```
sudo shutdown now
``` and see what happens

---

### Post by SoldierMedic on 2007-05-08
I'm having the same problem with an old HP Pavilion 4450 running Xubuntu Feisty Fawn.  The machine appears to be shutting down with no problems, it even turns off the hard drive.  Then the screen with the Xubuntu logo just stays there until I have to shut it down manually.

I tried the shutdown command with no luck.

---

### Post by smithman89 on 2007-05-08
Ive have this problem on Dapper Drake 6.06, it occurred after a sketchy re-install of ubuntu i did.  Basically just go for a terminal shutdown, or halt.  Shutdown didnt work for me, so whenever i need to shut the computer off, i  do:
```
sudo halt
```
The halt command will automatically close all open apps, and log off any users still logged in.  Make sure you dont do it while working on something, or else you may lose data.

---

### Post by SoldierMedic on 2007-05-09
The halt command has the same result as selecting shut down from the menu.  It goes through the entire shut-down process, turns off the hard drive, and then just hangs there.

Smithman, my install can be described as "sketchy" too.  I had to re-start the install process five times because the installer could never get beyond the "select and install software" portion.

Maybe I'll just reinstall Xubuntu and see if that solves anything.  Thanks for the help.

---

