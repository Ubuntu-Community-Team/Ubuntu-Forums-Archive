---
title: "Please help with game install in WINE"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-24
Hi
I just installed Wine from Synaptic.
The copied both Disks of SYBERIA onto my desktop as folders in order to install.

So I ran "wine setup.exe" and it started the install. When it asked for the second cd I click ok, the browsed to the folder on my desktop to access the second cd and it continued the install.

Now it's asking for the first CD again, and when I click OK the browse window does not come up so I cannot continue.

Any thoughts?

How do I uninstall wine installs?

Thanks in advance


EDIT >>> SORRY. My BAD. Stupid question. I should just insert the actual CD and not run it from a folder.

and about the uninstall....I should just google it I guess

Sorry

---

### Post by atria on 2007-06-24
Unfortunately wine is not perfect. That means not all windows programs can work perfectly with it.

Do make sure that you're using the latest version of wine from winehq.com though.

The c drive for wine is located inside /home/<user>/.wine
If you want to delete/uninstall just browse to that directory and delete the relevant files. You can even delete the entire .wine directory.

---

### Post by ROUBOS on 2007-06-24
OK thanks.
So If I want to add a nocd patch I just browse and find it there...

thanks for the help

---

### Post by atria on 2007-06-24
Yeah, just copy the nocd crack into your game directory (somewhere inside .wine)

Welcome, its my pleasure to help

---

### Post by ROUBOS on 2007-06-24
So if I delete the entire .wine folder does that remove wine????

---

### Post by ROUBOS on 2007-06-24
just hit 

wine Syberia.exe in terminal and did not start. Sound problems. :(
Is that how you run the game? By typing wine Syberia.exe

---

### Post by atria on 2007-06-24
Nope, it removes the configuration files as well as c_drive only. Just run winecfg to reconfigure wine and the directory will be recreated.

---

### Post by atria on 2007-06-24
Sound problems can often be solved through winecfg; you can choose different sound drivers there.

[edit]yeah thats the correct way to execute a windows program using wine.[/edit]

---

### Post by ROUBOS on 2007-06-24
The game does not run without my ATI Restricted Drivers Enabled.

The problem is that I need the ATI Restricted Driver to be disabled for Beryl to work.
When I enable it, games work but Beryl doesn;t:-(

---

### Post by techno-mole on 2007-06-24
to be honest i shut beryl down before i run a game, beryl like any program that uses alot of graphical type stuff will reduce the performance of the graphics in game if its running.

---

### Post by ROUBOS on 2007-06-24
well I just quit out of the Beryl Manager on task bar and Beryl effects still running

---

### Post by techno-mole on 2007-06-24
do you have beryl set to run at start up ? either way it doesnt really matter, change the window manager to gnome and then reload the window manager, then quit beryl, if it doesnt run at start up, quit it and restart x - ctrl -alt and back space and then run your game, i have mine to run at start up and i just change the window manager to gnome and then reload it, works for me.
to change window manager right click on the beryl icon, then click select window manager, then select gnome or what ever you want and then click reload window manager, that should shut it down enough to be able to run games, although i use an nvidia card, and this works for me, it may not work for you.

---

### Post by ROUBOS on 2007-06-24
Well the game runs without Beryl running. 
The thing is that I got Wine to work in a windowed environment. When I exit the game, the entire screen goes black and not just the windows wine environment forcing me to Ctrl-Alt-Backspace :(

---

### Post by techno-mole on 2007-06-24
im not an expert, but maybe the problem your having are down to the ati drivers ? i use an nvidia card and i generally dont have any trouble with this sort of thing, im not sure but i think that maybe the ati drivers arent too good, but like i said im no expert.
what you have described sounds like it may be a configuration problem some where ?
you need some one who knows about ati cards and drivers, they will be of more help than me, sorry.

---

### Post by ROUBOS on 2007-06-24
No problem. Will look into it. Thanks for your help.

---

