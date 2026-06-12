---
title: "[SOLVED] Problem Installing .package file (nogravity game)."
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by darolu on 2008-01-26
I'm trying to install No Gravity, is a shooter game, maybe most of you have seen it/played it.
I can't find it in any of Ubuntu's repositories, so I download it from the website: [http://www.realtech-vr.com/nogravity/](http://www.realtech-vr.com/nogravity/)
So following the instructions there and some other I found (ie here: [http://www.ubuntugames.org/NoGravity](http://www.ubuntugames.org/NoGravity) ) I'm supposed to install it very easily by double clicking the .package file, but when I did it tried to install using wine (nothing happened), then I right clicked and only found gedit as second option, in choose application the list showed me gedit, firefox, openoffice.org among others and wine, no one that seem to install a package, I tried with Synaptic, with install in the console (I only managed to create a copy of the file) and nothing works, any ideas on how to make it work normally (with the double click method) or any other way to install it?
Thanks in advance.

---

### Post by y-lee on 2008-01-26
See [How to install Linux autopackages in 4 easy steps]("http://autopackage.org/docs/howto-install/")

hope this helps :)

---

### Post by darolu on 2008-01-26
Thank you very much y-lee, that link helped, I could finally play it.
The problem was the execution permission, I simply had to click the little box and then double click the file.
BTW I really recommend this game, is really good. If you install the game with the above instructions it won't create a launcher in the applications menu you will need to follow this instructions translated from [http://www.ubuntugames.org/NoGravity:](http://www.ubuntugames.org/NoGravity:)
Press Alt+F2 or open a console and run: *gksu gedit /usr/games/launch-nogravity* it will ask your password and will open gedit, then paste/type this in the new text document and save the file:
```
#!/bin/sh
cd /usr/games/nogravity
./nogravity &
```
Then open your terminal (or Alt+F2 and clicking the execute in terminal option) and type this in:
```
sudo chmod a+x /usr/games/launch-nogravity
```
Then right click on Applications (top left corner) and click on Edit Menu, after that click on Games and on New Item, a window will pop up in the field name type No Gravity and in command: */usr/games/launch-nogravity*, you can add an icon if you like; then simply click in OK and that's it, you can launch the game from the applications - games list.

---

### Post by y-lee on 2008-01-26
Glad it worked and thanks for the tip :)

---

