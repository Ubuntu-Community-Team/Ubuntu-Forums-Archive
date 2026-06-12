---
title: "terminal embedded in desktop"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by DawnTreader on 2005-12-18
I have seen some screenshots where people have their terminal embedded in their desktop, how is that done?

I want it, I want it!

---

### Post by endersshadow on 2005-12-18
They just have transparent backgrounds.  In the terminal, go to Edit>Profiles, then click Default, and hit the Edit button.  Go over to the Effects tab, select "Transparency" and then move it all the way towards "None."

Voila.

---

### Post by DawnTreader on 2005-12-18
[QUOTE=endersshadow]They just have transparent backgrounds.  In the terminal, go to Edit>Profiles, then click Default, and hit the Edit button.  Go over to the Effects tab, select "Transparency" and then move it all the way towards "None."

Voila.[/QUOTE]

I have managed to get at least that much....

how about this [-<LINK>-]("http://ubuntuforums.org/gallery/showimage.php?i=1475&original=1&c=2")

---

### Post by ~LoKe on 2005-12-18
Install alltray then open the properties for your terminal launcher, go to the command box and add this :

alltray -x "gnome-terminal --window-with-profile=**your profile name here**"

EDIT : [This]("http://ubuntuforums.org/gallery/showimage.php?i=1551&original=1&c=2") is mine.

---

### Post by Wolki on 2005-12-18
[QUOTE=DawnTreader]I have managed to get at least that much....[/QUOTE]

It's the same. The menubar is hidden, and the window decorations (border and title bar) removed. You can do the first one directly from the menus, the other is (with gnome-terminal) a bit harder, you could (for example) use Devil's Pie (a window automation tool, see [https://wiki.ubuntu.com/Devilspie](https://wiki.ubuntu.com/Devilspie) or my How-to [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)) or alltray (a program that places things into the tray, see the transparent borderless pop-up terminal howto here: [http://ubuntuforums.org/showthread.php?t=81727](http://ubuntuforums.org/showthread.php?t=81727) this was used for the screenshot you posted).

All methods have a flaw, though: if you click on the show desktop button, the terminal is also hidden. :-/

---

