---
title: "not downloading"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by bearbigears on 2005-07-23
okay i am very new to linux and ubuntu. i have tried to download flashplayer, adobe reader, quicktime, etc. but i am not able to. i do not get a window with " where to download" desktop etc. i reloaded ubuntu os back onto my machine but it still will not work. also i looked in usr/bin/home but nothing is there. any suggestions?

---

### Post by PeP on 2005-07-23
[QUOTE=bearbigears]okay i am very new to linux and ubuntu. i have tried to download flashplayer, adobe reader, quicktime, etc. but i am not able to. i do not get a window with " where to download" desktop etc. i reloaded ubuntu os back onto my machine but it still will not work. also i looked in usr/bin/home but nothing is there. any suggestions?[/QUOTE]

1. if you use firefox to download, in Edit->Preferences -> Downloads 
you can set the folder where goes anything you download.

2. What the hell are you trying to do ??????? 
if a console makes you sick, use synaptics select what you want and get it
else just try in a console
sudo apt-get install flashplugin-nonfree
sudo apt-get install acroread acroread-plugin
forget quicktime it is not available on linux as far as I know, use mplayer or xine or vlc or totem or kaffeine or helix instead

3. the good thing with linux is that you do not have to find on the net/ buy , dowload, install a program

instead you search for something:
apt-cache search pdf reader

and then you choose one of the outputs and install it:
apt-get install acroread acroread-plugin

ubuntu downloads it and install it for you.

---

### Post by bearbigears on 2005-07-23
thank you very much PeP. this helped a great deal.

---

### Post by poofyhairguy on 2005-07-23
Welcome. This guide is your friend:

[www.ubuntuguide.org](www.ubuntuguide.org)

---

