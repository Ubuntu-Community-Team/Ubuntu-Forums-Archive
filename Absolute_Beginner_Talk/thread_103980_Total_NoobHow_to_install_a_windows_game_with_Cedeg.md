---
title: "Total Noob:How to install a windows game with Cedega and play with it ?"
date: 2005-12-15
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-12-15
How to install a windows game with Cedega and play with it ?
DirectX, For well known, age of empire 2 for instance...

Thank you

---

### Post by bjweeks on 2005-12-15
Did you install Cedega?

---

### Post by patrick295767 on 2005-12-15
from the deb files yes yes ... 
```
dpkg -i cedega-Installation-file.deb
```

Then, I dont really know what to do now

---

### Post by Mustard on 2005-12-15
Well when I installed Cedega it put an entry in my Applications menu, under Transgaming.  Has yours done that?

If not you can just type cedega into the command line and it will start up.  You should be presented with a pretty little gui, with which you can mount the installation CDs for your game and then browse to the relevant .exe file that installs the game and install it.

Included in the gui is an option to open up help files to show you how it works in more detail.

---

### Post by Arktis on 2005-12-15
First you have to run cedega for the first time so it generates its config files.

```
cedega
```

Next, intstallation and then running a game is just as simple.

```
cd /path/to/installer
cedega setup.exe
```
(or whatever the installer is called for the game you're trying to install)
cedega will install the game to a place inside the transgaming drive it creates in your home folder.

then
```
cd /path/to/game_exe
cedega game.exe
```

Easy enough.  Just make sure that 

a.) you have accelerated graphics drivers installed for your graphics card
b.) cedega supports the game you are trying to play

---

### Post by patrick295767 on 2005-12-15
[QUOTE=Mustard]Well when I installed Cedega it put an entry in my Applications menu, under Transgaming.  Has yours done that?

If not you can just type cedega into the command line and it will start up.  You should be presented with a pretty little gui, with which you can mount the installation CDs for your game and then browse to the relevant .exe file that installs the game and install it.

Included in the gui is an option to open up help files to show you how it works in more detail.[/QUOTE]

I got sthg concernign langage problem ... no gui ... I maybe have a conflict somewhere with my langage from deb file and ubuntu in english ... ?

---

### Post by patrick295767 on 2005-12-15
I'll try tonight. Thank you **[SIZE="4"]very [/SIZE]**much ! 
 
By the way, Is there a version of the program totally free or opensource ?

---

### Post by patrick295767 on 2005-12-15
Is there some people using cedega for free ? (every months)

---

### Post by patrick295767 on 2005-12-15
I found this webpage concerning free cedega ... :
[http://ubuntuforums.org/archive/index.php/t-32589.html]("http://ubuntuforums.org/archive/index.php/t-32589.html")

---

### Post by sethmahoney on 2005-12-15
You can also do a GUI install by starting cedega from the applications menu and then hitting the "Install" button.  Be careful, though, if you've installed Wine: When you insert the CD for the game, Ubuntu will open a nautilus window that displays the contents of the CD.  Do NOT double-click on the installer in that window - if you do so, it will attempt to install the game into your Wine folders, not your cedega folders (which makes it a little more difficult to find and run).

---

### Post by patrick295767 on 2005-12-16
Hi, 

I tried ... it's working !
  
I installed Myth II, without any problem ! As fast as in windows ! No differences. 
  
I tried to use cedega for microsoft apps like bibliorom for instance ...
And it's not working, .. . why ?
  
Is it only for directx apps games ?
  
Greetz'
 
Pat'

---

### Post by Perfect Storm on 2005-12-16
Some works, other needs a bit tweaking and then there's the programs which won't work no matter what (at current state).

---

### Post by sethmahoney on 2005-12-16
[QUOTE=patrick295767]Hi, 

I tried ... it's working !
  
I installed Myth II, without any problem ! As fast as in windows ! No differences. 
  
I tried to use cedega for microsoft apps like bibliorom for instance ...
And it's not working, .. . why ?
  
Is it only for directx apps games ?
  
Greetz'
 
Pat'[/QUOTE]

Depending on the app, you may have more luck getting it running with Wine than with Cedega.  Both apps, I believe, have lists of Windows software known to work with them (and sometimes instructions on how to get them to work).  I don't have the URLs handy, but a google search or a quick search of either homepage should turn them up quickly.

---

### Post by patrick295767 on 2005-12-16
little question: how to uninstall my myth II program now ??

thank you

---

### Post by sethmahoney on 2005-12-16
[QUOTE=patrick295767]little question: how to uninstall my myth II program now ??

thank you[/QUOTE]

Open up Cedega and right click on the "folder" you installed it to.  Click delete.

---

### Post by patrick295767 on 2005-12-16
[QUOTE=sethmahoney]Open up Cedega and right click on the "folder" you installed it to.  Click delete.[/QUOTE]
  
I installed age of empire conqueror expansion !
thta's amazing how fast it is !!!
  
I installed cedega 4.4.3-1, from copying in /usr ... nothing in menu
In order to remove file, I got in /home/user 
the installed folder, that I brutally with krusader : DELETE !!
  
For sure, it's not there.
I guess that wasnt best solution but it's less MB ... 
  
If u have an advice: Which games should I try to install now to be amazed of gaming in linux: Old good and New ones !??

---

### Post by patrick295767 on 2005-12-16
Is it possible to install programs like apps like dictionaries or microsoft office with cedega ??
  
Is it mainly for games . Why games are workign preferably and not apps ?
It's rather amazing prg !
  
Is it a bit laggy for you ??

---

