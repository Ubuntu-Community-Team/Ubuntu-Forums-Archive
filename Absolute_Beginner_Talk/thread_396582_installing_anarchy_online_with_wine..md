---
title: "installing anarchy online with wine."
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by noob_saioke45601 on 2007-03-29
hey all, my roomie loves AO and i share my computer with him. he want's to play again so we downloaded it and tried installing it from the desktop via (wine ./Desktop/AOinstall17.1.1_EP0_live_nointro/install.exe)

and have gotten this error upon trying to open the installer.

```
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"H:\\Desktop\\AOinstall17.1.1_EP0_live_nointro\\install.exe": Bad EXE format for

```

i also noticed it says bad EXE... we downloaded by torrent and completed sucessfully with no errors so anyone know whats wrong?

---

### Post by Omnios on 2007-07-10
problems solved. If you get a cannot access C: delete ./wind and run wincfg to make a new C. directory.

 The game will not install in the base wine install and I found a script that helps install stuff for wine that works really well/

 The script is here                 [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
Right click and save link as.  winetricks.sh and make it executable.

 Running the command    sh winetricks

 This will show a list of installable stuff which can be installed using.  sh winetricks corefonts where corefonts is the file being installed.
 
 I installed the DCOM and the ms installer before installing the game.

 I read this here on Mepis [http://www.mepis.org/docs/en/index.php/Wine_setup](http://www.mepis.org/docs/en/index.php/Wine_setup)

 Also the install seems to be a bit dirty in that when you launch setup.exe it states to run install.exe which works. I'm having a problem with the included Xfire program as the language install poped up behind the main installer window. This is solvable by clicking on the task bar and choosing move and moving to a empty place on the sreen. Anways launching the game with wine right now and will post results in case of a crash. Also did install with desktop affect off as the install screens where unreadable.

---

### Post by Omnios on 2007-07-10
k it want to launch but i am getting stumped on a res and vid driver screen. Anywone have any ideas?

 Solved choose a lower res and double clicked on the wine vid driver.
 
 Going to go play so laterz.

Log in and patching working,,, Laterz dude

 Had a problem patching it froze up and now I am doing a reinsatll
Might have to use manual patches.

---

### Post by Omnios on 2007-07-10
Dam I seem to have a little devil looking over my shoulder. I managed to gt it installed and  the graphics config worked before and I managed to log in and it crashed at the updater after choosing to upgrade. 

 Well now it does not want to even install properly or run. I might have to reinstall wine or find a way to kill the regestry. 

 Ultima online sucked and sucks so I hope I can get this to work.

 K got it to install and run again. 

 Solved the vid set up by opening winecfg and clicking vid and closing which is wierd

 I have to patch so ging to have to do a manual patch as a winhq page said that autopatch did not work in wine.

---

### Post by Omnios on 2007-07-11
Got it working posted on the anarchy online how-to.

[http://ubuntuforums.org/showthread.php?t=291330](http://ubuntuforums.org/showthread.php?t=291330)

---

### Post by bINSkeeter on 2007-07-20
I tried to run Anarchy Online Setup.ex_ and this is the error message i get please someone help.:confused::(

---

### Post by Omnios on 2007-07-21
> **bINSkeeter said:**
> I tried to run Anarchy Online Setup.ex_ and this is the error message i get please someone help.:confused::(

did you run wincfg to make a fake c directory?

---

### Post by bINSkeeter on 2007-07-24
i guess not...how do you do that? haha sorry im newb

---

