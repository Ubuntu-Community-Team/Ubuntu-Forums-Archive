---
title: "Rollercoaster Tycoon 2"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by oneouncebrick on 2008-03-19
hey there! i play rollercoaster tycoon2 and i waswondering how i could install it on my xubuntu laptop? beginner talk please.. lol =P:KS

---

### Post by oneouncebrick on 2008-03-19
is there a way to play it, and save my games ? and install it properly on xubuntu, better yet? will my laptop be able to handle the game... i have a 520,000kb of RAM and 14.5 gb of un-used memory.. its an old ibm think-pad from year 2000

---

### Post by Captainm on 2008-03-19
Rollercoaster Tycoon 2 seems to work in [wine]("http://www.winehq.org/") so we'll install that first.

Open a terminal and type (or cut and paste) the following pressing Enter after each line 
```
sudo aptitude install wine
winecfg
```

Now we'll install Rollercoaster tycoon.

```

wine /path/to/installer.exe
```
If you're installing from cd that line will look something like
```
wine /media/cdrom/setup.exe
```

That should be it!

---

### Post by oneouncebrick on 2008-03-19
hmmm, ill install wine then, thanks so much! =D however, do i have to run wine in order to play rct2? 

or is it a program i run it through... what does it do

---

### Post by mattk132 on 2008-03-19
Without getting too much into expert stuff, wine is a layer that works to make windows programs work in ubuntu.  To install you're game simply go to your disk under places and then double click on setup.exe.  Wine let's you run .exe files in linux.:)

---

### Post by oneouncebrick on 2008-03-19
hey after i installed wine i typed the winecfg code, and it brought up a box that was the settings, and a bunch of processors for windows?.... its xubuntu.. linux is not one of the options to select? what do i do...

---

### Post by oneouncebrick on 2008-03-19
oh i get it.. i just clicked windows 2000 lol thats wat my comp origionally had.

---

### Post by oneouncebrick on 2008-03-19
also, is it possible to install rct2 expansion packs? think wine will let me do this?

---

### Post by oneouncebrick on 2008-03-19
hmmm.... wine is installed.... but now how do i install rct2??

---

### Post by Captainm on 2008-03-20
You can issue the command I described above or, and I forgot about this :P, you can just doubleclick on the rct2installer.exe and wine should install it. Same with the extension packs.

---

### Post by mattk132 on 2008-03-20
YOu can try to use Wine for every .exe file.  However, it isn't guaranteed to work.

---

