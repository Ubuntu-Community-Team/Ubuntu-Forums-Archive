---
title: "Windows emulator?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by kristoffer2200 on 2006-04-24
I have heard that I need an windows emulator to install games. I heard I need "Cedega", but that costs money. Somebody knows somethings thats free?

---

### Post by bluevoodoo1 on 2006-04-24
"wine" is what you're looking for.

[http://www.winehq.com](http://www.winehq.com)

[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
will guide you through the download/install

---

### Post by mybootorg on 2006-04-24
Look into "WINE".  I havent tried it  yet myself and I understand it's not so simple to configure depending on the game you wish to run.  But I remember seeing a webpage that broke down all of the most popular games: Battleground, World of Warcraft etc and showed you how to get them running, and what the gotchas and known bugs are.

Personally, I play World of Warcraft and though I lubs me some Ubuntu, playing WoW in Ubuntu -- while possible -- just doesn't seem to make much sense to me.

#1 - it's not going to run as efficiently. period. no matter what anyone tells you.

#2 - anytime the game gets patched -- with WoW this is a pretty common occurance -- it's likely to screw up your ability to play it over WINE, if not keep you from playing altogether.

#3 - why emulate XP when you can Dual boot?  Make yourself a small "games" boot partition and install a bare bones, stripped down version of XP.  Then install your games and you're set.  It's a Microsoft world via DirectX where games are concerned these days.  I dont like it any better than you do, but if you can beat em, join em.

---

### Post by kristoffer2200 on 2006-04-24
I got xwine know. But how can I use it? I have the CD in the CD-room and then?

---

### Post by pbaehr on 2006-04-24
mybootorg,

Dual Booting is a pain in the ***. Granted, sometimes it is unavoidable, but if it means spending an extra few hours setting it up or learning something new that's a little outside my comfort zone so that I don't have to restart the computer whenever I want to run certain software it's good in my book.

Lucky for me the only game I play on the computer is Unreal Tournament 2004 and that runs natively on Linux. Also, I think the "if you can't beat 'em, join' em" philosophy is exactly the reason WINE was spawned. Linux will probably not overtake the MS market share in the near (or even not so near) future so WINE is an attempt at adapting to what's out there.

---

### Post by kristoffer2200 on 2006-04-25
[QUOTE=kristoffer2200]I got xwine know. But how can I use it? I have the CD in the CD-room and then?[/QUOTE]
BUMP!

---

### Post by jethro10 on 2006-04-25
[QUOTE=kristoffer2200]BUMP![/QUOTE]
Wine itself can be installed graphically from the package manager.

when installed go to [www.winehq.com](www.winehq.com) for compatability lists, lots do run but lots dont.

from terminal you can access setup by typing winecfg

to "install" a windows program called install.exe type "wine install.exe"

that should be enough to get you going.

A comment above said it was an emulator, it isn't. It's performance is almost always as quick as native windows.

Jeff

---

### Post by kristoffer2200 on 2006-04-25
[QUOTE=jethro10]Wine itself can be installed graphically from the package manager.

when installed go to [www.winehq.com](www.winehq.com) for compatability lists, lots do run but lots dont.

from terminal you can access setup by typing winecfg

to "install" a windows program called install.exe type "wine install.exe"

that should be enough to get you going.

A comment above said it was an emulator, it isn't. It's performance is almost always as quick as native windows.

Jeff[/QUOTE]

Thx m8! *ENOUGHLETTERS*

---

