---
title: "All Openoffice programs call the word processor."
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by lateb on 2007-08-03
I installed Xubuntu as a dual boot on an old (P2/350 256m)system with win98se. Openoffice loaded the word processor in the initial load.  The word processor had a display problem, which I fixed by putting a later 32M Nvidia card in.  However, I have now loaded the other programs from Openoffice via the add/remove programs and now all the programs within Openoffice call the word processor.  I did a remove and reinstall, same result.  I am just starting to learn my way around in linux and don't know where to go for this problem.

---

### Post by Hospadar on 2007-08-03
you should check the launcers for the individual programs and see that they are set up properly

the way open office launches it's different apps is with command line arguments, for example, to start OOo impress, you would run ```
ooffice -impress <whatever other args>
``` It may be as simple as these arguments being wrong or not existing at all in the launcher.  try editing the launchers to see if they are correct and change them if not.  you can also launch the different apps with seperate commands like ```
oobase
ooimpress
oocalc
```
etc.

If you can't get them to work, try reinstalling, or running the proper commands from the command line.  If they work properly off the command line, you should be able to just make your own launchers for them so you can click instead of having to open a terminal every time.

If you do a ```
man ooffice
``` it will show you all the different commands for different parts

---

### Post by lateb on 2007-08-03
I am very new to Linux, can you lead me through the process of creating launchers? I deleted OO from SMP and reloaded, but it still calls the wrong program.  I can call them manually.

---

### Post by lateb on 2007-08-03
Sorry, I jumped the gun, I figured it out and now have all modules of OO opening properly from a file folder on the desktop.  Thanks for your help!

---

