---
title: "Bit Torrent Client"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Tyrael_Odium on 2006-07-19
Ok, I am new to linux, so you may see my name pop up in these forums a lot in the next little bit, and so far i have gotten a lot of help on these forums, so i will continue to come back as long as there are people who can answer my questions. Now here is my problem. I am trying to get a bit torrent client installed, i started with azureus because i like it the best, so i went online and opened up my bookmark of [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper) and i was following their little instructions to get azureus installed and it didnt work the error message i got is as follows

-E: Couldn't find package azureus

The command was this

-sudo apt-get install azureus


so i tried to go out and download an azureus installer and run it, and i cant get an executable, i can only open it from the command line, and it will not respont to my mouse clicks, so i decided to give up on it. The next client that i started to work on was bittornado because it was right below the azureus one, and i did the first command
-sudo apt-get install bittornado
and that one worked, but when i did the second command
-sudo apt-get install bittornado-gui
it did not work the error message that i got looke like this
-
Package bittornado-gui is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
-
, so i went out online again to download another installer thingie for linux instead, and i messed that up just as good as i did the azureus. if somebody could lend me a hand it would be greatly appriciciated

---

### Post by meng on 2006-07-19
Do you have extra repositories enabled? I think you need universe enabled to get azureus. The guide you used does have a section on adding extra repositories, even though it's not specifically mentioned in the section on azureus.

As I recall (from my own experience), the dapper-repository version of Azureus works but has some important bugs (no panel icon, and crashes on next run if not shut down cleanly - easy to do when there is no panel icon!) and the easiest way to fix this is to install from repositories first, and secondly overwrite the Azureus2.jar file with a more recent version.

Good luck with it.

---

### Post by byen on 2006-07-20
Hey Tyrael_Odium,
Why not [try Automatix]("http://ubuntuforums.org/showthread.php?t=190025")? It is a tool that would help install the programs you have mentioned as well as a ton of other tools you might want later.. Please check [this link]("http://ubuntuforums.org/showthread.php?t=190025"). I have used it to install Azureus and have not had any issues. 
Good luck!
byen

---

### Post by taurus on 2006-07-20
Another vote for azureus from me.

---

### Post by Redcard on 2006-07-20
KTorrent for me.

It offers inline searching for torrents from the popular sites.

---

### Post by Drakkor on 2006-07-20
Will Ktorrent work with Ubuntu gnome ? Guess not,just for KDE
Anyway I'm getting real tired of all the Azureus problems,as you can see from the screenshot,
I have downloaded the update and then restarted,only to have the update needed box come up again !! ](*,)

---

### Post by FuzZy2006 on 2006-07-20
uTorrent is way better than KTorrent and easier than azureus and it is easy to configure with wine.

---

### Post by taurus on 2006-07-20
> **Drakkor said:**
> Will Ktorrent work with Ubuntu gnome ?

Yes, it will.  You can run KDE's apps in Gnome or vice versa...

---

### Post by meng on 2006-07-20
> **Drakkor said:**
> Will Ktorrent work with Ubuntu gnome ? Guess not,just for KDE
Anyway I'm getting real tired of all the Azureus problems,as you can see from the screenshot,
I have downloaded the update and then restarted,only to have the update needed box come up again !! ](*,)
Yeah I have that too, that bit of the update doesn't seem to stick. I haven't tried disabling the updater yet, that will be my next step. Anyone else encountered this problem?

---

### Post by fhqwhgads on 2006-07-20
Check this post for the answer: [http://www.ubuntuforums.org/showpost.php?p=1253562&postcount=7](http://www.ubuntuforums.org/showpost.php?p=1253562&postcount=7)

Azureus needs priveleges to apply the updates.

---

### Post by meng on 2006-07-20
Thanks for this.

---

