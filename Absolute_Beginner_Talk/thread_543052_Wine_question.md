---
title: "Wine question"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Insomnia777 on 2007-09-04
Hi guys, it's nice to join the club under the same pinguin :)

I installed Ubuntu 7.04 (FF) on my comp, with the Nvidia drivers, Compiz-Fusion, Emerald, and Wine. Since I play Tales of Pirates I use it a lot, but I have noticed certain things like: special graphics do not appear (the look like a black moving blur) and the custom mouse of the game does not appear.

How can I go about to making sure I can fully play it, should I review my driver version, or install Cedega or Cedega CVS?

---

### Post by toidi on 2007-09-04
Just checked on the wine app database and also on the cedega website.  It reads like you will have issues whether you use wine or cedega :(

[http://appdb.winehq.org/](http://appdb.winehq.org/)  search for tales of pirates there.

And also [http://games.cedega.com/gamesdb/categories/view.mhtml?gametype=12](http://games.cedega.com/gamesdb/categories/view.mhtml?gametype=12)

Personally I have found wine to be better at everything I have thrown at it compared to cedega.

---

### Post by Insomnia777 on 2007-09-04
Ye so I see there, but I'll test it out right away, if anything does come up non-funtional what do you suggest I do? BTW how can I go about getting or updating to the newest version of wine? (idk if I have it ^^)

---

### Post by Insomnia777 on 2007-09-04
Hmmm I found a way to fix the cursor but the graphics is another prob, can anyone help me translate this in easier english? ^^


A little experimentation shows that I can get in-game cursors instead of that X cursor. See Bug List for patch or
appdb.winehq.org/appview.php?iVersionId=7440
for Patching Instructions (You'll need to change the wine version to the more recent ones).

Instructions taken from Command & Conqueror 3 HOWTO
==Patching for Cursor Support==(Lines changed to refer to ToP and Wine 0.9.43)
To get proper cursors in the game, you need to patch Wine, which can be done as follows.
1. Download Wine ( prdownloads.sourceforge.net/wine/wine-0.9.43.tar.bz2 ) and the cursor patch archive ( bugs.winehq.org/attachment.cgi?id=5962&action=view ) to the same directory
2. Unpack the patch archive to a directory called 'cursor_patches_20070428'. There should be an option for this if you right-click on the patch archive in the file manager, but you can do it manually with 'mkdir cursor_patches_20070428; tar -xvjf cursor_patches_20070428.tar.bz2 -C cursor_patches_20070428'
3. Unpack the Wine archive through the file manager or with 'tar -xvjf wine-0.9.43.tar.bz2'
4. Enter the Wine directory with 'cd wine-0.9.43'
5. Apply the cursor patches with 'for i in `ls ../cursor_patches_20070428`; do patch -p1 < ../cursor_patches_20070428/$i; done'
6. Update wineserver with 'tools/make_requests'
7. Configure Wine with './configure --prefix=$HOME/wine-top' (--prefix is optional), where you can choose another install path if you want to. If it displays any errors and you are unable to fix them yourself, post the error message here, without the full console output
8. Build Wine with 'make depend && make'
9. Install with 'make install'
- Delete the Wine source with 'cd ..; rm -rf wine-0.9.43'
- Now you can run the game by substituting the 'wine' commandd with '$HOME/wine-top/bin/wine'
(Taken from [[http://appdb.winehq.org/commentview.php?iAppId=4888&iVersionId=7531&iThreadId=23836]("http://appdb.winehq.org/commentview.php?iAppId=4888&iVersionId=7531&iThreadId=23836")

---

