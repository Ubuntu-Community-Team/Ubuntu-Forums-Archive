---
title: "no wine shortcuts?"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Meow27 on 2008-02-11
hi, im using an old IBM thinkpad with feisty 7.04 installed

i recently installed the WINE version from the available source via synaptic. it was version 9.33 or something.
i upgraded it from the instructions the wine official website gave me, but after i installed it, i have no shortcuts for wine. i can only access it via terminal but i cant manage to get wine to have shortcuts (it has shortcuts on me desktop using 7.10 gutsy)
anyone have any solutions? thanks
-meow

---

### Post by Joeb454 on 2008-02-11
Restart X (Ctrl + Alt + Backspace) I've found this usually adds the required shortcuts in my menu's :)

---

### Post by Meow27 on 2008-02-11
that merely restarts. ill rephrase my issue

i dont have shortcuts to run wine (because the install failed to get them on my menu or something) and im trying to get them in my menu >.>

---

### Post by mc4man on 2008-02-11
after the upgrade did you run  ```
wineprefixcreate
``` ?

---

### Post by Meow27 on 2008-02-11
i havent, i tried it and i dont see a difference :/

---

### Post by Mze on 2008-02-11
Run:

locate wine

Did you install WINE with sudo?

You might as well use synaptic to remove all traces of Wine and then use the instructions on the Wine website for you version of Ubuntu

---

### Post by Meow27 on 2008-02-11
answer is yes for sentence 3 and 4

---

### Post by gsmanners on 2008-02-11
0.9.33 is rather old. You might try version 0.9.51 or newer.

---

### Post by Mze on 2008-02-11
this [thread]("http://ubuntuforums.org/showthread.php?t=690224") should solve your problem.

---

### Post by Meow27 on 2008-02-28
couldnt find what i needed

ill restate what i am looking for

these wine menus that can be seen here:
[img]http://ubuntuforums.org/attachment.php?attachmentid=60896&d=1204057452[/img]

---

### Post by mc4man on 2008-02-28
Don't have feisty any more so going from memory - the menu item should have stayed behind when you uninstalled .33 and installed .xx ?. Did you ever delete the menu from edit menus?
If not try right clicking on applications>edit menus and see if wine is listed in the show box - if so and unchecked try checking. If you can't check or not listed post back
sometimes clicking revert also works - may have some unintended results though
What version did you upgrade to?
note:
If you had deleted the menu previously there is a different procedure to restore it

---

### Post by Meow27 on 2008-02-28
i installed .55

.33 had no separate menu

i didnt delete any menu before because there wasnt any and finally, i cannot check the wine menu because it doesnt exist :(

---

### Post by mc4man on 2008-02-28
I'm gonna fire up this old laptop with feisty and ck. meanwhile - If you go into home folder(with ctrl h) there is a folder .config, inside should be a folder menus. Inside of that should be a file - applications.menu - see if there's an entry for wine. Also there may be a folder - applications-merged - if so see if there's a wine menu in there

edit: from a fresh install of feisty wine (any version)_ doesn't_  create a wine menu item in applications until you install a program into wine - preferably something that installs to program files. Then you'll see a separate menu item for wine (may have to restart). After that when you upgrade the menu will stay in place. 
I wouldn't use .55 - has issues - try .54 - .56 will be available shortly as a .deb

---

### Post by Meow27 on 2008-03-06
ok the menu exists now :) thanks

---

