---
title: "Removing WIne"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Taras on 2007-12-13
Hello everyone, i been using Wine for some of my favorite games, many games work fine and then 1  extra game i installed and it doesn't work, i tried to remove it from Wine Uninstallation Software, i did, it says its been deleted, i even removed even from the Wine C drive the folder but it still shows in my  wine menu options that its there, alotugh it doesnt work becouse it was deleted for some reason it still shows it, i even tried to remove wine from synaptic still same result its there, Wine doesnt get deleated

IS THERE ANY COMMAND THAT I CAN PUT INTO TERMINAL THAT WILL COMPLETELY KILL WINE ?

Thanks for reading

---

### Post by jaybombalous on 2007-12-13
I don't use wine because of this, its annoying. The one good thing wine did teach me is that no headache is worth a game.

just to be clear on this, not once in the 20 or so times that I tried wine did it ever work correctly.

---

### Post by whazooo on 2007-12-13
> **Taras said:**
> Hello everyone, i been using Wine for some of my favorite games, many games work fine and then 1  extra game i installed and it doesn't work, i tried to remove it from Wine Uninstallation Software, i did, it says its been deleted, i even removed even from the Wine C drive the folder but it still shows in my  wine menu options that its there, alotugh it doesnt work becouse it was deleted for some reason it still shows it, i even tried to remove wine from synaptic still same result its there, Wine doesnt get deleated

IS THERE ANY COMMAND THAT I CAN PUT INTO TERMINAL THAT WILL COMPLETELY KILL WINE ?

Thanks for reading

After Uninstalling your program, Look in your 
~/.local/share/applications/wine/Programs
Delete the offending program directory
the program will no longer show up in your wine menu

---

### Post by CatKiller on 2007-12-13
It seems quite harsh to remove Wine just because one game doesn't work, especially when you say that you've got other that do. Well, did, I guess. If you don't want to see the Wine menu items, the easiest way is to right-click on the menu bar and select "Edit Menus" and then uncheck the box next to the Wine menu item.

Otherwise, if you wish to actively remove Wine's menu items, they are largely kept in ~/.local/share/applications/wine

---

### Post by CatKiller on 2007-12-13
> **jaybombalous said:**
> just to be clear on this, not once in the 20 or so times that I tried wine did it ever work correctly.

You must be very unlucky. I've had many successes with Wine.

---

### Post by daengbo on 2007-12-13
Remove the program's menu file under:
.config/menus/applications-merged/wine-Programs-<name of program>.menu

That is where programs install to the wine menu. Why they don't remove from there during uninstallation, I don't know.

---

### Post by CatKiller on 2007-12-13
> **daengbo said:**
> Why they don't remove from there during uninstallation, I don't know.

Because Windows installers are crap. It's not like they remove their Start Menu entries on uninstallation from Windows either.

---

### Post by HotShotDJ on 2007-12-13
> **jaybombalous said:**
> just to be clear on this, not once in the 20 or so times that I tried wine did it ever work correctly.For me, WINE has been a mixed bag.  Sometimes it works, sometimes it doesn't.  Fortunately, I haven't had any real use for Windows programs for quite a while now.

---

