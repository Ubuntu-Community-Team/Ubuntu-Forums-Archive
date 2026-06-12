---
title: "Really weird thing happening (missing tracks in amarok)"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by roach of discord on 2008-01-12
Hi, for the past few days something really weird has been happening. It *seems* ever since I updated to kde4..amarok (the stable version) does not find all of my collection when it scans.  Like..some albums will only have 3 or so tracks..some albums wll be gone, etc.  And what's even weirder..say one album has 4 missing tracks..if I add JUST that folder as my collection, it will find all of the files in it. If I scan my whole music folder, they will go missing again.  I had this problem on kubuntu so I tried SuSE..same problem. If I scan my entire music folder with JuK all my files are found fine.

Any ideas as to what could be wrong? All of my music files and folders are on a seperate harddrive and mounted in /media/shared.  I believe they are on a reiserfs partition.  Could this maybe be some weird permission issue or something?  Could it have something to do with KDE4.0?

Thanks.
-Joe

---

### Post by geirha on 2008-01-12
It sounds odd. Could you quit amarok if you have it running, then open a terminal and run amarok from there. Then rescan your collection, and see if it gives any error messages in the terminal.

---

### Post by roach of discord on 2008-01-12
Thanks for the reply.

I did that, and got:

lunar-raven@linux:~> /opt/kde3/bin/amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

I don't see any obvious error that would relate to that.

I rescanned..still missing files all over the place.  most albums show..but there are usually a few (or more) files not there.

Very weird =[

---

### Post by przeuj on 2008-02-08
Same problem here...

---

### Post by geirha on 2008-02-08
I think you'll have better luck by posting a bug report at amarok's website. [http://amarok.kde.org/](http://amarok.kde.org/)

---

### Post by nynoah on 2008-02-08
yeah my Amarok started doing this too.  I am not sure if it is because of KDE4 being installed.  But I do know that it has to do with Amarok not being able to recognize files inside a directory.  I noticed that when check say the folder marked music, it will only recognize files that are not in folders.  It will not recognize an MP3 that is inside a subfolder or my music file.  The long drawn out way to fix this, is to check every folder individually, crappy way to fix that huh.  But that is the only way I could figure it out.  Hope my insight lends some ideas to someone with more knowledge.

---

### Post by przeuj on 2008-02-12
Looks like it is OK now... Not sure what happened but the collection is now back.

What about the rest of you?

---

### Post by erikf154 on 2008-05-03
I have the same problem, running hardy KDE4 remix. The problem seems to be independt of permissions and format.

I've tried the following:
- rescanning the collection (didn't get any error messages on the console)
- updating the collection
- deleting the database file (collection.db in .kde/....apps/amarok)
- deleting the entire amarok profile directory (.kde/....apps/amarok)

Nothing really helps. Everytime something is missing. I have about 19000 songs, but amarok finds only 12000 (the number various from 12500 to 11500 every time I rescan my collection, weird!)...

There's a thread about this on the amarok forum on their homepage as well: [http://amarok.kde.org/forum/index.php?topic=15215.0;prev_next=next](http://amarok.kde.org/forum/index.php?topic=15215.0;prev_next=next). Doesn't seem like anybody's detected what the problem is though.

---

