---
title: "wine &amp; windows mounting questions"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2005-12-25
well, ive gotten wine to run on my ubuntu system, but i've noticed that it is somewhat laggy. is this normal? i have an amd64 3000 and 512mb memory, so it seems like it should be able to run just fine. and is it possible to run google desktop search with wine?

also, I would like to set up my windows boot to be able to view and possibly write to my linux partitions. how do I go about doing this?

one last question. for ut2004, how do you install this to run natively on linux?

---

### Post by HyperNewbie on 2005-12-25
windows can't read linux file systems(ext3/2/whatever).

probably the only way for them to communicate is fat32, as linux can read/write it and so can windows.

um....yeah same for me wine runs games pretty slow, so its pretty normal i guess. u can see the scanlines running through displaying each frame for half life for me ...

---

### Post by GuitarFingers on 2005-12-25
Wine can be a bit laggy, but that really depends on the program.  I'm unsure about google desktop search as I've never tried it.  You may want to have a look at Beagle instead, its a similar product for linux.

If you're looking at games in the main as your reason for needing windows you may want to consider having a look at the [Transgaming]("http://www.transgaming.com/") version of wine which is optimised to run quite a few Windows games.

As HyperNewbie has already said, windows can't read any form of Linux file sytem.  I run vmware with a windows session which is fine for most apps except for games and other applications using graphics acceleration. Which is unfortunately where most people come unstuck.

As for ut2004, there is a native linux version available for download. Save it to your home folder and execute the file and it will install itself quite happily and works perfectly (at least it does for me!). Details are available [here]("http://www.unrealtournament.com/ut2004/downloads.php")

Hope all that helps.

GuitarFingers 

*PS: The accuracy and content of all posts is directly proportional to the amount of liquor consumed prior to posting. It's Christmas evening here so all bets are off...*

---

### Post by The Warlock on 2005-12-25
[QUOTE=iand675@gmail.com]one last question. for ut2004, how do you install this to run natively on linux?[/QUOTE]

On CD1, there's something called install-script.sh or something similar. I don't rememer the exact name. Run it with sudo and it will step you through the install process.

---

### Post by MetalMusicAddict on 2005-12-25
[QUOTE=iand675@gmail.com]well, ive gotten wine to run on my ubuntu system, but i've noticed that it is somewhat laggy. is this normal? i have an amd64 3000 and 512mb memory, so it seems like it should be able to run just fine. and is it possible to run google desktop search with wine?[/QUOTE]
WINE is one of those weird things. Some things work great some dont. Its trial and error.
> also, I would like to set up my windows boot to be able to view and possibly write to my linux partitions. how do I go about doing this?
It ***IS*** possiable to read/write to Ext2/3 from windows with this: [Ext2 IFS]("http://www.fs-driver.org/"). Ive used for 6 months with no problems. See [THIS]("http://www.ubuntuforums.org/showthread.php?t=107311") thread for both sides.
> one last question. for ut2004, how do you install this to run natively on linux?
On the DVD or last disc of the CD install there is a script to install it on linux.

---

