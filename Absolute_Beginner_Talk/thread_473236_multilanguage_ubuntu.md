---
title: "multilanguage ubuntu?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by mr32123 on 2007-06-13
I was just wondering, is there a way to install 2 languages and be able to switch between the two with something so simple as some sort of key combo?

---

### Post by starcraft.man on 2007-06-13
> **mr32123 said:**
> I was just wondering, is there a way to install 2 languages and be able to switch between the two with something so simple as some sort of key combo?

Ok, not sure exactly what you mean... If your referring to spell checking in applications that per the application. Firefox and Open Office both have dictionaries you can install for multiple languages and switch between them.

To install dictionary in Firefox:
[1) Go here install switcher.]("https://addons.mozilla.org/en-US/firefox/addon/3414")
[2) Go here and install dictionaries of your choice, don't install more than you will use.]("https://addons.mozilla.org/en-US/firefox/browse/type:3")
3) Restart firefox, switcher is in bottom right.

To install dictionary in OO:
1) Go File Wizard > Install new dictionaries.
2) Follow the wizard and start DIscoo
3) Hold ctrl down when selecting dictionaries to select mulitple ones at each entry.
4) Restart OO, there is a language selector in one of the toolbars.

If you mean keyboard support then you want System > Preferences > Keyboard > Layouts. Add all the languages you want here per your region. Then go to the "Layout Options" tab. I believe here you will find the group shift/lock behavior, configure this however you prefer to switch layouts.

Thats it I think, Enjoy :D.

---

### Post by mr32123 on 2007-06-13
I mean more like in the beginning when you are installing ubuntu, it gives you a few different languages to choose from.  Is there any way to install it in more than one language or be able to switch languages on the fly after the installation?  I mean such things as the system menus, etc.

---

### Post by starcraft.man on 2007-06-13
> **mr32123 said:**
> I mean more like in the beginning when you are installing ubuntu, it gives you a few different languages to choose from.  Is there any way to install it in more than one language or be able to switch languages on the fly after the installation?  I mean such things as the system menus, etc.

Thats more complicated I believe. First you have to go to System > Administration > Language Support. Now find and install any languages you want to use.

Then, (I'm not sure about this part, I only use english) I think you have to manually edit the user groups languages. I don't know where or how to do this though. I believe if you edit the option at the bottom (default language) and set it to the one you want you'll be able to make a new user with the language you selected. Editing might be harder and I don't know. This isn't an on the fly thing, no OS can change whole languages on the fly as far as I know. You certainly can't do it in Windows this easily.

Try that, if not... someone else come with answer please.

---

### Post by johnraff on 2007-06-14
I've got English installed (for me) and Japanese for my wife. (using "language support")
Once languages are installed you can choose from a dropdown menu when you login. It was pretty easy- I didn't have to edit any config files by hand.

Don't think you can switch in the middle of a session, though it might be possible to "export" a certain "locale" to a particular program as it starts up...
(This gets above my head.)

---

### Post by mcduck on 2007-06-14
YEs, just install language packages for all languages you want, and then in the login screen click on the 'session' (or 'language' depending on your login screen theme) button and select which language you want to use.

As far as I know only keyboard layout can be changed on-the-fly, changing the actual language can only be done at login screen.

---

