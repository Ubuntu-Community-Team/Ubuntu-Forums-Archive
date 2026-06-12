---
title: "pro/engineert tryout wine edgy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-10-22
I keep doing this. Silly questions!

I just downloaded the 'tryout' version of Pro/Engineer and installed it using Wine. The installation went well (HUGE program) but I can't access it. Applications>Wine>Programs>PTC>Pro EngineerTryout Edition>Pro Engineer Tryout Edition.
I have a Desktop icon as well but no result. 
I recall a similar scenario when I loaded AutoCad 2000, but that was from a CD, and I could swap a lot of dlls from the CD if I remember correctly.
Basically I have forgotten the Terminal commands which get me into Wine and play with it from there. I should have taken better notes ...

Apologies,
Michael.

---

### Post by bubbalouie on 2007-10-22
try:

> wine "C:\Program Files\Some app folder\program.exe"

On the assumption you installed to a default directory.

Assuming you want to configure wine, try:

> winecfg

I do strongly recommend you have a play with cross over office however. As a tip, the 'bottles' can be made to run with the regular wine too if you decide that you want to run the cross over installs with a newer version of wine (this works even after cross over is uninstalled as crossover is based on wine). I do exactly this myself, I went to **~/.cxoffice** and copied the bottle with my copy of office xp into my program files folder, the example command I use to run it is below:

> cd /home/bubbalouie/Program_Files/Office_XP_Pro
env WINEPREFIX="/home/bubbalouie/Program_Files/Office_XP_Pro" WINEDEBUG=-all wine "C:\Program Files\Microsoft Office\Office10\WINWORD.EXE"

You can take this a step further, you can associate powerpoint files etc with the wine application so that you can double click a file to open it (for me open office is the default, but work sometimes requires I use MS Office, so it is in my right click menu), I made a script with the following in it [word.sh]:

> if [ "$1" = "" ]; then
	cd /home/bubbalouie/Program_Files/Office_XP_Pro
	env WINEPREFIX="/home/bubbalouie/Program_Files/Office_XP_Pro" WINEDEBUG=-all wine "C:\Program Files\Microsoft Office\Office10\WINWORD.EXE"
else
	FILENAME=Z:$(echo $1|sed 's/\//\\/g')
	cd /home/bubbalouie/Program_Files/Office_XP_Pro
	env WINEPREFIX="/home/bubbalouie/Program_Files/Office_XP_Pro" WINEDEBUG=-all wine "C:\Program Files\Microsoft Office\Office10\WINWORD.EXE" "$FILENAME"
fi;
 

A little KDE trickery with some pretty icons courtesy of google and it is as though word, excel and powerpoint were all native applications.

Anyway, after all that, cross over will make setting things up easier, you can use wine with the result after if you find cross over to be a bit much. Sadly wine will not get some things to run by itself, cross over can sometimes address this (when you need to make a judgement call on a purchase).

I still recommend a purchase of cross over office as they have done a lot of work to make these things possible and are a major contributor to the wine project, also they make everything much easier than wine (Whilst I don't need it myself because I only wanted MS Office, IE6, Rowley Crossworks, SWCAD III & ARMWSD, as a matter of course, I plan on getting a copy for my girlfriend so she can move away from windows as she is forever getting viruses etc). If you need clarification (sorry for being scant on some details), just sing out.

Good luck :)

Ryan

*EDIT: I just checked out what Pro/Engineer is, you can get a linux version...

---

### Post by Enverex on 2007-10-22
> **MichaelSM said:**
> I keep doing this. Silly questions!

I just downloaded the 'tryout' version of Pro/Engineer and installed it using Wine. The installation went well (HUGE program) but I can't access it. Applications>Wine>Programs>PTC>Pro EngineerTryout Edition>Pro Engineer Tryout Edition.
I have a Desktop icon as well but no result. 
I recall a similar scenario when I loaded AutoCad 2000, but that was from a CD, and I could swap a lot of dlls from the CD if I remember correctly.
Basically I have forgotten the Terminal commands which get me into Wine and play with it from there. I should have taken better notes ...

Apologies,
Michael.

chdir to the directory where you installed the application and run it with the syntax
wine whatever.exe
Then paste the output of the terminal in a "code" box here.

---

### Post by MichaelSM on 2007-10-25
Thanks to all for your suggestions.

What I didn't mention was that I have XP in Virtualbox, and I'd disabled at first instance any hope of getting XP on line for all sorts of reasons which shouldn't be hard to imagine.

In the end I re-enabled web access to XP on Virtualbox and ProEngineer is now installed on XP/Virtualbox.

However, it is a prick of a program (ProEngineer Tryout Edition) in that it only wants to run on-line and gets niggly about cookies, which I have enabled with Firefox in XP, but that doesn't seem to help.

No major drama. I couldn't afford the 'real' version anyway, but it would have been nice to have a play.

It's just funny in a way to re-visit Windows on-line and for insurance of sorts to wear AVG etc. just like the bad old days.

Unfortunately ProEngineer discontinued their support for Linux machines back in May. I would have liked to try their Unix program with Ubuntu. 

Thanks for listening/reading.

Mike.

---

