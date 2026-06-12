---
title: "What exactly is WINE?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by osprey_criminal on 2006-11-05
So I've been messing around with WINE, and I still can't get anything to work very well.

Do I need to have a Windows box/partition to run it?  What kind of commands do i need to run?  

Specifically, I can't get Brood War with Battle.net access running, and everytime i try to install Winamp, I get a font error.  I haven't even tried to install CS2 because of these problems with WINE.

I'm sorry to ask all this, but winehq doesn't seem to offer much solid information.  Thanks for any and all help.

---

### Post by MasterOfDisaster on 2006-11-05
Wine does not need a windows partition or even a windows license (with the exception of some 3rd-party DLLs for legal reasons).  It will create a hidden partition in your home directory, and it will have the same file hierarchy as normal windows...  To see what programs work and what programs don't look at [http://appdb.winehq.org/](http://appdb.winehq.org/).  For running it, basically type 'wine progname.exe' where progname is the name of your program (note if you're not in the same directory as the file you will have to add the path).  Other commands are 'winecfg' for general application settings.

---

### Post by aysiu on 2006-11-05
A slight correction: it does not create a hidden *partition* in your home directory.

It creates a hidden *folder* in your home directory.

Bottom line: it's a way to run native Windows programs in Linux.

Your best bet, of course, is to find native Linux programs whenever possible; otherwise, why are you even using Linux if you want all Windows programs?

Instead of WinAmp, for example, try XMMS.

---

### Post by Zeroangel on 2006-11-05
You have to first navigate to the directory that you want to run the program in```
cd /home/yourusername/wherevermyprogramisstored/
wine program.exe
```It's kind of annoying to do that every single time you want to launch the program, so I personally use a shell script to run those commands instead of messing with the command line:

Creating a shell script is easy:

1) Create a file called (whateveryouwant).sh
2) Use a text editor and put in your commands such as:
```
cd /home/yourusername/wherevermyprogramisstored/
wine program.exe
```3) Right click on the shell script and change its permissions to 'executable'
4) Click to launch the script, and it will run those commands for you.

If it doesn't work, than your app might not be compatible with WINE, or you need to run 'winecfg' and change some settings.

---

### Post by aysiu on 2006-11-05
Whoa, whoa, whoa! You don't have to create a shell script.

One command handles it all.

For example, this one command, if you have Windows' FileZilla installed using Wine, will launch FileZilla: ```
wine "z:\home\*username*\.wine\drive_c\Program Files\Filezilla\Filezilla.exe"
``` You can create a launcher or keyboard shortcut for that command. There's absolutely no need to *cd* into the directory first and then run the command.

More details on how to use Wine:
[http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine)

---

### Post by Zeroangel on 2006-11-05
Oh.... :-k

Thanks :KS

---

### Post by osprey_criminal on 2006-11-05
Thanks for helping me understand!

---

### Post by hearnden on 2006-11-05
If you're mainly interested in using WINE for games, then maybe think about just having a proper Windows partition.  Unfortunately Windows still beats Linux convincingly for gaming, and if an Ubuntu user has Windows installed somewhere, then there's a good chance that it's for gaming.

WINE for games is kind of like editing MS Office documents in Open Office.  It does damn well considering how much help the developers get, but it doesn't quite cut the mustard compared to the original.  If you want to play games in an environment that they were not built for, then try to be forgiving for things that don't quite work in WINE.  Brood War did run under WINE for me, but jerkily and with no sound.

---

### Post by justifier on 2006-11-05
wine doesn't allways work and i will back up the other posters here, if you want to game use windows, because at the moment there are no "windows syle" games wit a big user base, dual booting is allways good tho!!!

---

### Post by aysiu on 2006-11-05
Dual-booting is the sure way to go for games, but you may also want to look into Cedega, which is a Wine derivative focused specifically on commercial games.

[http://www.transgaming.com](http://www.transgaming.com)

---

### Post by bodhi.zazen on 2006-11-05
[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

