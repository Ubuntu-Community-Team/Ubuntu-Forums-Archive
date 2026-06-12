---
title: "Sessions commands"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by try2lickurelbo on 2007-06-20
Hey guys,
I'm a big noob with Linux and I'm just now starting to customize my desktop, can anyone tell me the commands for sessions to have all my gDesklets pop up and also my cairo-clock?  Plus, can anyone recommend some other programs etc. to modify my desktop and make it look much, much snazzier than my brothers mac? ;)

---

### Post by EagleRock on 2007-06-21
You can right click on the panel you want to add stuff to and select "add to panel," as it will give you options to add the applets you want.

---

### Post by Ziox on 2007-06-21
To make apps automatically start, go to: System > Preferences > Sessions

then hit new and then type in the command used to start that application (gdesklets and cairo-clock).  

Also, if you want a mac bar that's much better than the one offered by gdesklets, use avant-window-navigator. Google it and you should be able to find their repository for feisty.

gDesklets bar doesn't have real transparency, it simply copies part of your background then paste it as its own.  Avant on the other hand has true transparency, like cairo-clock.

BTW, if you have trouble logging in after adding cairo-clock to the session manager, remove it from autostart.  It caused some breakage for me.

Edit: if you've added the apps to autostart but they don't show up upon login.  Then make sure you have the correct permission for the folder ~/.config/autostart.  Use the following code to correct the problem, if it happens:  sudo chown -R <username> ~/.config

---

