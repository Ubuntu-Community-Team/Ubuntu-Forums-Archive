---
title: "Insalling wine"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by antidartan on 2007-06-08
I am a complete newb , but I have read that I need wine for what I want to do. I have downloaded it and it is on my desktop but I don't have a clew how to install it or get it working. when all is said and done I want to run halflife but I'm sure there will be more uses. Thanx for your help



email
[email]dwalker5@rochester.rr.com[/email]

---

### Post by yabbadabbadont on 2007-06-08
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Those are the instructions to use with Ubuntu.

---

### Post by mark. on 2007-06-08
lol i wanted to do the same thing to run cs1.6 :D

---

### Post by mariosx on 2007-06-08
> **mark. said:**
> lol i wanted to do the same thing to run cs1.6 :D

lol ! i'm installing windows XP in virtualBox RIGHT NOW, just to be able to play Call Of Duty 2 :)

---

### Post by antidartan on 2007-06-08
those are the instructions? I went there down loaded wine and had no idea what to do with it/ . The problem with linux instructions is they assume you no were to go and were to put stufff, oh yeah and what you should download

---

### Post by antidartan on 2007-06-08
have been using windows for years , this is a shock to the system

---

### Post by yabbadabbadont on 2007-06-08
Those instructions tell you to copy and paste into a terminal window....  ;)

---

### Post by supersonicdarky on 2007-06-08
alternatively, you can download the package and install it by double clicking

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html) (get the apropriate version)

---

### Post by Nythain on 2007-06-08
best to install wine through their repository... wich those instructions on that site are for how to add their repository and install via apt-get...

basically if you want the really simple im gonna hold your hand directions, here we go... open up terminal (im assuming you know how to do this, if not i cant help you, i dont use gnome, wich you probably do)
once you have a terminal open type this
```

gksudo gedit /etc/apt/sources.list

```it will ask you for a password, put in your password
that should open a file up with a bunch of lines starting with deb [http://whatever](http://whatever) the junk.

scroll down to the bottom of the file and add this line (making sure to change feisty  to your version of ubuntu you have running)
```

deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main

```save the file and close gedit
now back to terminal type this
```

[I]wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
[/I]
```[I]
then type (bah, somewhere in teh copy paste set me to italic, lame)
```

sudo apt-get update
sudo apt-get install wine

```if all went well it should then be installing the latest version of wine
[/I]

---

### Post by Nythain on 2007-06-08
it just occured to me, if you are having trouble installing it, you might end up needing some help running it... here we go, pretty simple

once its installed, in terminal type
```

winecfg

```
that will initialize wine, set up all the directories, and from this GUI you can make any system changes your need, though you probably wont have to mess with anything, cept possibly changing your sound, and maybe what version of windows you want wine to emulate (i would stick with 2k, its the most stable for wine)

feel free to close the gui whenever you are done looking around and changing any settings

to use wine from now on, its easiest to use it from terminal by typing something similar to this
```

wine ~/drive_c/Program\ Files/uTorrent/utorrent.exe

```
in that example, im am using wine to run the utorrent.exe
thats easy enough, but how did i install utorrent you say... its pretty much similar in the fact that you type wine /path/to/the/install.exe
lets say i saved the utorrent install.exe to my my home directory
```

wine ~/utorrentinstall.exe

```

another usefull bit of information for when you are trying to find out where wine installed something to... wine installs into a hidden directory in your home directory
in terminal it can be seen like this
```

cd ~
ls -a

```
and can be accessed like this
```

cd ~/.wine

```
notice hidden directories in linux start with a .

in your file browser of your desktop environment there should be an option somewhere to "Show Hidden Files"

another note, to type spaces in terminal you need a \ before the space like in the example
```

wine ~/.wine/drive_c/Program\ Files/uTorrent/utorrent.exe

```
notice i have a \ after Program, then the space... thats important... \ alone isnt a space, it just lets linux know a space is coming up

i think thats about all i can think of on running wine at the moment, hope that helps once you get it installed

---

