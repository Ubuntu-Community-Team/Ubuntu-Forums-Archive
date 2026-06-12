---
title: "Launcher icons and the limiting thereof"
date: 2005-11-04
forum: Absolute Beginner Talk
---

### Post by Griff on 2005-11-04
When changing the icons for the launchers, it appears as though png's are ok.  However, when browsing to folder where my freshly made png icon is, it is greyed out.  Is there a size limiting problem here?  Don't see why some png's are ok and others are not...  It's 256x256 btw.

---

### Post by Kyral on 2005-11-04
I thought most icons are like 86x86...I may be wrong though

---

### Post by Griff on 2005-11-04
I can resize it not problem if that's the issue.  Guess i'm wrong to assume the panel would autoresize it?  I'll try reducing it to said size and see what happens.

edit: thanks for the Keitaro avatar btw, *it eases the soul*

---

### Post by SilentCacophony on 2005-11-04
The panel *does* resize icons to fit the height of the bar, but I don't know if there are any limits to the size. 256 x 256 seems pretty large for an icon, though. Most of the ones I use are between 32 x 32 and 64 x 64.

---

### Post by mcduck on 2005-11-04
there is some weird bug or something with choosing icons in Breezy/Gnome. If you choose just any icon you can when you make the shortcut, save it, and then edit the launcher again you can choose any icon you want. (when you make launcher only icons from the default theme folder work, but when you edit existing launcher any image works)

Somebody here had other way to do it, but I can't remember it and anyway this should work..

---

### Post by Griff on 2005-11-04
Yea, 256x256 is pretty fat.  Reduced it to 64x64, but for some reason i still wasn't allowed to use the image for an icon.  Funny thing though, i noticed that anything not in /usr/share/pixmaps wasn't allowed either.  Jumped to the command line, sudo moved that thing (first time having to sudo ;) ), and now it works.  Seems strange to me to have to do that, but oh well, it works.  Also, if you hit the browse button, it initially brings up the above directory, but it won't let you use the icons listed anymore, but they were initially allowed :confused:. What's going on here?

---

