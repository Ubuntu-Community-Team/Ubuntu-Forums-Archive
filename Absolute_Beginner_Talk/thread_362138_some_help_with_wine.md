---
title: "some help with wine"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-15
Hello
ive been wondering whether its worth installing wine, so today ive put it on, but after its installed its recommended that you run winecfg from terminal, i presume it has to create certain folders and such like, so i go into terminal and type winecfg and the system locks up totally ? the only way to do any thing is to push the restart button, i take it that this is not meant to happen, so does that mean it wont run on my system ? every time i try it does the same.
im using edgy (not the 64 bit version)
cheers

---

### Post by Bloch on 2007-02-15
wine will run straight away. Type 
wine --help
(there are two dashes there)

or 
wine notepad
to see if it works. Then grab a few simple .exe files - card games or whatever - to see how they work. Do you dual-boot? Do you have windows XP on a different partition? If so you can grab any .dll files if wine says it needs them.

wine is installed in the 
.wine directory - it is a hidden directory so you need to tick  View =-> Show hidden files on your file browser (I presume you are running standard ubuntu, i.e. witht he default gnome desktop)
You will also see your virtual C drive in this folder.

I have never had to use winecfg - but if it is not working for you it indocates somehting has gone wrong witht he instakllation

---

### Post by Maestro23 on 2007-02-15
[http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

---

### Post by techno-mole on 2007-02-15
it seems wine doesnt want to run on my system.
ive tried installing using automatix, and after automatix has installed it it gives the message to run winecfg, which locks up the system.
ive been to the website - [http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index) (thank you) and installed wine the way they give instructions and it does exactly the same, that is it locks up the system, wine makes no attempt to run what so ever after its installed, and all the commands have the same effect, they lock the system up ?
cheers

---

### Post by techno-mole on 2007-02-15
hello
this is a kind of a rant about ubuntu and wine, i tried installing wine this morning, it went on fine, but it wont run and any command i type just locks the whole system up and the only way to get out is to restart the whole system.
ive tried eveything, ive tried all the different versions of wine and all do exactly the same thing, so as far as i can tell wine will not run on my system no matter what, which in itself is not that much of a problem, but i was wondering if i could use it to play some games, but no luck, ive spent a couple of hours trying to find a solution but i havent really found anything that helps, ive done extensive reading on the wine hq website but to no avail.
:confused:

---

