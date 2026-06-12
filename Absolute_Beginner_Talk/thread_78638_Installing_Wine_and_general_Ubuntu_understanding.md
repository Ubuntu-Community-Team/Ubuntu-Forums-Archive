---
title: "Installing Wine and general Ubuntu understanding"
date: 2005-10-18
forum: Absolute Beginner Talk
---

### Post by Mathias-K on 2005-10-18
Hi, when i tried Red Hat Linux three and a half years ago, i felt it to be far behind Windows XP, but i recently gave it a chance again.

Ubuntu is fine-looking and smooth, but i have had some trouble understanding it.. I've got MSN and music working, but getting Wine is still a problem.

I read a guide to installing it saying that it could be done easily using the Synaptic Package Manager, so i followed the instruction and ended up with around 20 or so packages. The problem is that when i mark some of the packages for installation, the system automatically marks some other ones for deletion. I have no clue as to which packages to choose, as they are named "winesetuptk", "wine-dev", "libwine-cil" and so on. This codetalking is a part of Linux that i do not understand at all, and i simply dont get why there isnt just a Wine installer that puts everything in place.

Can you help me get my games up and running? :)

---

### Post by ecobuntu on 2005-10-18
Just mark "wine"
apt-get is smart enough to get the other packages you need.  

Also to start a file:

cd /in/to/directory/of/interest

wine setup.exe 
     or
wine sweetlookingwindowsgame.exe

PS - Red Hat sucks.  Stay away from RPM based distros.

---

### Post by Mathias-K on 2005-10-18
Thanks for the help, dude.

I put my Dawn of War cd in my drive, typed 

cd /media/cdrom0/
wine setup.exe

and up went the InstallShield Wizard as in Windows. Then i clicked Next to start installing, and an error came:

Unhandled Exeption
Error Number: 0x80070057
Setup will now terminate

Hmm.. I guess there are some other things, i should be aware of using Wine? Is it required to configure it to not bring these errors, or is it game-specific?

Thanks in advance

---

### Post by jerrygofixit on 2005-10-19
funny, i've spent 2 days trying to get Steam to work with anything (wine,cvswine,cedega) and didn't bother to register, but felt compulsed to register after I saw this(and i'm a 'newbie')

You need to install the DCOM98.exe stuff for Windows under Wine (i'd go back and find all the links for you but it's pretty late and i'm tired, sorry, but search the forums for dcom98 and you'll find it) as well as the Installshield stuff (again, search forums for InstmsiA.exe) and to my understanding you may need some native .dll files for certain things to run properly (winecfg in console). That's the best help I can give at this hour, good luck.

---

### Post by Mathias-K on 2005-10-19
[QUOTE=jerrygofixit]
You need to install the DCOM98.exe stuff for Windows under Wine...[/QUOTE]

Thanks for the direction, but i cant get it to work.. Is there no guide or package  that just installs Wine for WinXP gaming?

---

