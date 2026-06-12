---
title: "WINE locks my system"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by fickendichdu on 2007-09-11
I installed WINE a few weeks ago and everytime I go to click on WINE file.  My system completely freezes up and I have to hold the power to shut down.  I think I am missing a package.  I saw an error about missing the X11 driver.  Thanks for the help.

---

### Post by southernman on 2007-09-11
I know nothing about wine, but I know that whoever does and wants to help you, they'll need more specific info... please repost with all the pertinent info you can relating to specific errors you get and so on, including your system specs.

Good luck getting this working for you.

---

### Post by fickendichdu on 2007-09-11
Ubuntu 7.04 
AMD Athlon 3300
1gb memory
200gb hard drive
Intel 945 graphics. 

There is not much more I can post about the problem.  Except that when I click on Wine File my system locks and I am unable to even do ctrl alt backspace.  I have removed Wine and reinstalled  but I still have the same problem.

---

### Post by Daveth on 2007-09-11
what windows programs are you running under wine? What happens if you type 

```
wine and-the-windows-program-name
```

into a terminal? Does it still freeze your system? What is the answer to

```
wine --version
```

as this may help as well. Are you launching wine from the Applications menu, or from a desktop shortcut?

---

### Post by fickendichdu on 2007-09-11
Yes wine faile if i do WINE mine

wine-0.9.44

---

### Post by Daveth on 2007-09-11
what sort of program is "mine" - will help us out (or me at least) to look it up!

---

### Post by fickendichdu on 2007-09-11
Minesweeper.  Also I haver troubles with Outlook Xp and Adobe Flash.

---

### Post by Daveth on 2007-09-11
you should not have any problem at all with minesweeper- see

[http://appdb.winehq.org/appview.php?iVersionId=290](http://appdb.winehq.org/appview.php?iVersionId=290)

which rates it as platinum. As for Outlook, have you looked at Evolution as an alternative?

Did you follow the first steps in

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

when you installed wine, or rather did you break any of the do not break rules? It might be best to start over with wine and re-install, so

```
sudo apt-get remove --purge wine
```

which, as Cogadh notes, " should remove all traces of the previous Wine install (except your .wine directory) and you should be able to reinstall it normally."  It might be worth trying out the older wine version in the Ubuntu repositories, certainly for Minesweeper. Then get into the folder with the minesweeper.exe file, and launch the wine mine command in a terminal within that same folder. And see what happens....

---

### Post by fickendichdu on 2007-09-11
I installed Wine via the synaptic package manager.  Not sure how I could have messed it up.  I use evolujtion but i am trying to see why it locks up so i have tried other apps.

---

### Post by fickendichdu on 2007-09-12
I am looking for some help with this dilemma.  I have tried removing anything that had the word WINE from Synaptic and reinstalling it but I am still having lock ups.  If nothing else could a mod move this thread to another location.  I may have posted in the wrong spot by mistake.

---

### Post by Cannaregio on 2007-09-15
Maybe this question is very stupid: are you 'using' wine correctly?

Wine is not an emulator. You have _to install the windows program you want to run_ using wine.
The program will therefore be installed inside the fake "C: drive" that has been created by wine.
You start your program (best way) navigating to that folder
you have to enable hidden files to see the ```
.folders
```
Your folder will be under ```
home/your_user/.wine/drive_c/Program Files...
``` etc
and then you will have to run in a terminal (so that you can exactly see what happens) the following command:
```
wine name_of_your_program
```
mind you, this must be run INSIDE the correct folder where the windows exe you want to run dwells

even better, as command (very verbose):

```
env WINEPREFIX="/home/father/.wine" wine "C:\Program Files\Your_target_folder\Your_target.exe"
```

And then you'll see what's really going on.

Sorry if you knew all this already.

---

