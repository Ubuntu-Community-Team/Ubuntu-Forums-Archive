---
title: "Where are my games???"
date: 2006-05-29
forum: Absolute Beginner Talk
---

### Post by KarmaKing on 2006-05-29
hello all,

I have recently installed, through synaptic, some games to try:

Atank, Igeneral, gnuchess, scorched earth.

And a few other programs and can't seen to find them.  I go to apps--games and they are not there, even though I have their boxes checked through they a being shown as installed through synaptic, boxes checked in the Add Application, and are checked in the menu editor

do I have to install or download something more??

Also I am looking for kodo

thanks in advance

---

### Post by johnc4510 on 2006-05-29
Try: ctrl+alt+backspace  to restart and see if they show up

---

### Post by KarmaKing on 2006-05-29
[QUOTE=johnc4510]Try: ctrl+alt+backspace  to restart and see if they show up[/QUOTE]
rebooted and restarted, nothing, but still present in the proper menus

---

### Post by ComplexNumber on 2006-05-29
[quote=KarmaKing]hello all,

I have recently installed, through synaptic, some games to try:

Atank, Igeneral, gnuchess, scorched earth.

And a few other programs and can't seen to find them.  I go to apps--games and they are not there, even though I have their boxes checked through they a being shown as installed through synaptic, boxes checked in the Add Application, and are checked in the menu editor

do I have to install or download something more??

Also I am looking for kodo

thanks in advance[/quote] sometimes programs don't get isntalled in the menus. its usually if there is an desktop entry file in the installation which gets installed in /usr/share/applications.
fire up your terminal and type the name of the game on the commandlien to see if it runs. if it doesn't, it will give some erros as to what the problem may be. 

btw if you don't have a small (but VERY useful) application installed caled bash-completion, isntall it now.  the reason why its useful is that it comes in hand at those times when you can't remember the full name or spelling of an application or viariable or whatever when typing it on the command line. for example, you may want to see what other commandsa re associated with nautilus, so you type in "naut" on the command line, then press the TAB button twice to give all the options. it may bring up:
"nautilus"
"nautilus-actions"
"nautilus-help"

(these are just made up example just to show you what i mean). but seriously, install bash-completion if you haven't already.

---

### Post by johnc4510 on 2006-05-29
I don't have these particular games, but I have had some in the past that just didn't show up in the menus. You can launch them from the terminal, or you can add to one of your panels, Run an Applications. To do this, right click on a panel and choose  add to panel and look for the run an aplications icon, and add it. You can also choose in the add to panel and then make a custom launcher for your panel for each of the games

---

### Post by KarmaKing on 2006-05-29
[QUOTE=johnc4510]I don't have these particular games, but I have had some in the past that just didn't show up in the menus. You can launch them from the terminal, or you can add to one of your panels, Run an Applications. To do this, right click on a panel and choose  add to panel and look for the run an aplications icon, and add it. You can also choose in the add to panel and then make a custom launcher for your panel for each of the games[/QUOTE]
tried this a second ago and it doesn't show the programs as available.

and all but kodo do not work through the terminal.

should uninstall all and reinstall?  I remember installing some of them in pairs?

---

### Post by johnc4510 on 2006-05-29
How you installed them, in pairs, singlely or all at once should not make a difference. You can try uninstalling the ones that don't work and then reinstalling them, it might work. Probably not. As for the bash-completion, I think it has already been written into the bash program so don't worry about that. Good luck and keep fiddling.

---

### Post by ComplexNumber on 2006-05-29
**KarmaKing**
install an application called alacarte. its a superb menu editor thats better than the oen that comes with breezy. it will alllow you to enter an entry for the insalled games. just enter the name, the command to run the game (usually the name of the game), and an associated icon.

---

### Post by Sef on 2006-05-29
Thanks complexnumber.  I had the same problem as KarmaKing, only I have downloaded it, but forgot I had it. :lol:

KK: To download it, just go into Synaptic.

---

### Post by nalmeth on 2006-05-29
I may be wrong, but I believe most games end up in /usr/share/games

Perhaps they will show up in xfce-appfinder

in a terminal: sudo apt-get install xfce4-appfinder

---

### Post by ComplexNumber on 2006-05-29
> Thanks complexnumber.  I had the same problem as KarmaKing, only I have downloaded it, but forgot I had it.
glad that i inadvertantly helped ;). but reading back KarmaKing's question, i seem to have misread it slightly :mrgreen:


> I may be wrong, but I believe most games end up in /usr/share/games
many of them do. not all, though. some end up in /usr/local/games/bin and /usr/local/bin and /usr/bin.

---

### Post by KarmaKing on 2006-05-30
[QUOTE=nalmeth]I may be wrong, but I believe most games end up in /usr/share/games

Perhaps they will show up in xfce-appfinder

in a terminal: sudo apt-get install xfce4-appfinder[/QUOTE]

thanks for that, I found them all, but...

I was playing Igeneral and the problem is it is just the game itself and I had to download campaigns into the campaign folder, but it won't give me access.  How do I do that?  How do I sign in as root or gain write access to the restricted folder?

---

