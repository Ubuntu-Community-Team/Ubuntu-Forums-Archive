---
title: "Playing Games"
date: 2005-11-12
forum: Absolute Beginner Talk
---

### Post by taterknight on 2005-11-12
I really want to play a game on this computer,[http://www.soldat.prv.pl/]("http://www.soldat.prv.pl/"), Can someone explain exactly what I need to do in order to play.  Installation, other progrmas needed, etc.

---

### Post by teaker1s on 2005-11-12
as it's for windows you would need wine emulater to run it seach forums for wine and you'll see how its done

---

### Post by etc on 2005-11-12
You're going to need to install wine.  I got your game working in it using Wine 0.9.1 which is not in the Ubuntu repos, so we'll need to use the Wine Repos.

First off you should download the game from [here]("http://flab.llsc.us/soldat13.zip"), and save it to your desktop.  Right click it, and click extract and you should get a file called "setup.exe" sitting there.

Now we need to be able to use the new wine, so lets add the Wine Repositories into your /etc/apt/sources.list, so open a terminal and
```
sudo gedit /etc/apt/sources.list
```
Then add this to the bottom of the file then save
```
deb http://wine.sourceforge.net/apt/ binary/
```
Which will point apt to download wine from the wine repos.

Then open Synaptic from the System -> Administation menu, and click reload.
or from the terminal
```
sudo apt-get update
```

Then search in Synaptic for "wine" and when you find it, right click the entry, and click Mark for Installation, then click apply
or from the terminal
```
sudo apt-get install wine
```

After it downloads and installs, go to your desktop and double click setup.exe, it should automatically be opened by wine, but if not, right click it and select 'open with' and choose wine.
or from the terminal
```
cd ~/Desktop
wine setup.exe
```
And follow the wizard.

After it installs it should place a bunch of launchers on the desktop, they should work and you should be able to play it, if not then open a terminal and 
```
cd ~/.wine/drive_c/Soldat/
wine Soldat.exe
```
Then play

here a little encouragement
[[IMG]http://img186.imageshack.us/img186/797/screenshotsoldatexe1mi.png[/IMG]](http://imageshack.us)

---

