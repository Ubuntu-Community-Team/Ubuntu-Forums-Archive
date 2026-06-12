---
title: "Wine , Winecfg , Installation Help"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by tempest152 on 2006-12-05
Greetings all, 

New to the Ubuntu forums, but I have been searching on this topic a while and havent found anything particular to my situation, but I did find other ideas to try for installation.. But to start..


I run Ubuntu 5.10 Breezy, with Knome desktop, and aptitude package manager.   I downloaded and installed Wine via Package manager, through the listed repository on WineHQ for my particular version of Ubuntu.

After installation I open terminal and type wine, and it gives me the syntax help, I run winecfg, and the terminal throws errors about not finding L"c:/*.*" and a couple other similiar messages, but winecfg still opens.   I click "Drives" and it tells me to make sure and add "C" drive ect..  I do autodetect, then try to apply and it gives errors in the terminal about drive mappings..  I have found out thry research that the "fake c" drive should be located in the home directory, as of today, and winecfg was not looking there..

Sorry for the vagueness of my errors messages, but I am at work away from my machine.  I can post the real deal later if no one comes up with anything.

After all that, my main questions are,  will winecfg need to be nudged on the drive mappings by manually setting c: to ~/.wine/c/ , and d: to the dosdevices directory ect..  

Will it not work to map CD as /media/cdrom0?

And has anyone encountered these errors on winecfg after applying configuration?


Any suggestions much appreciated..

---

### Post by IMELucky on 2006-12-05
Download and install winetools (just google "winetools")

It will create your wine directory and install some common software to let you run windows programs, and configure your wine setup

reply back if u need more specific directions and goodluck

---

### Post by tempest152 on 2006-12-05
> **IMELucky said:**
> Download and install winetools (just google "winetools")

It will create your wine directory and install some common software to let you run windows programs, and configure your wine setup

reply back if u need more specific directions and goodluck


Yes I read about winetools..  So can I run winetools on top of my existing WINE install?  Or do I have to uninstall WINE and start over with wine tools first?

---

### Post by IMELucky on 2006-12-05
you won't need to reinstall wine, but you should delete delete your ~/.wine directory

rm -rdv /home/(username)/.wine

Download winetools from here
[http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz)

and unpack (right click on it -> extract here)

open the terminal and navigate to the directory that you extracted winetools to and type

sudo ./install.sh

and then when the install finishes type

wt

This will create a wine directory and there will be menu driven installers for common windows programs.

I should point out that while Wine can run lots of software, it does have a lot of bugs so don't be surprised if everything doesn't work right

---

### Post by Bloch on 2006-12-05
Check that wine is working by getting some simple .exe file - notepad.exe or freecell.exe

Open a terminal and move (by using cd) to the same directory as the .exe (Or else dump the .exe in your home directory, where the terminal opens by default)

Now enter 
wine freecell.exe

so at least you can see wine is running.
Next download some freeware .exe and do the same - if they have to install they will find or create your "C:" drive. This is a directory which wine regards as a virtual C drive. 
It is in the .wine directory - this is a hidden directoty so you will need to click View > Show hidden files on the nautilus top menu

---

