---
title: "[SOLVED] How to use extended ASCII characters"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by notbitmonk on 2007-08-07
I would like to use characters like the following: áéíóúñÑü¿ whenever I type in [K/X]Ubuntu.  In Windows this is done by using the ALT key and a three code number.  Is there a similar way to do it in [K/X]Ubuntu?

---

### Post by jnorthr on 2007-08-07
would have expected the same thing to use the ALT key. It may depend more on the codepage used by your editor (gedit or kate)

---

### Post by Anicka on 2007-08-07
Here you find some info: [http://en.wikipedia.org/wiki/Unicode#Input_methods](http://en.wikipedia.org/wiki/Unicode#Input_methods)
To find out which code to use go to the character map in Applications -> Accessories.
So in gedit: ctrl+shift+u00e5 for å. In KDE, I don't know how it works, but that is the GNOME way.

---

### Post by expatCM on 2007-08-07
just thinking beyond your question ..........   is there a particular reason why you have asked this .....  for example are you wishing to have Spanish language support on your system ...  or is it just for incidental use?

---

### Post by AZzKikR on 2007-08-07
> **notbitmonk said:**
> I would like to use characters like the following: áéíóúñÑü¿ whenever I type in [K/X]Ubuntu.  In Windows this is done by using the ALT key and a three code number.  Is there a similar way to do it in [K/X]Ubuntu?

Somewhere in the preferences of Ubuntu (Keyboard preferences?) there is an option which let you type characters like ©áßøðäå¾‘ú¡²³¹£ etc by just pressing AltGr + (Shift) + Letter/Number. I can't exactly recall what it was called, but I've enabled it at installation, and I am 100% sure it can be enabled after installation too. I'll check at home.

---

### Post by AZzKikR on 2007-08-07
System -> Preferences -> Keyboard

Tab "Layout"

U.S. English International (with **dead keys**).

---

### Post by briandotcom0 on 2008-01-10
Ctrl+shift+u can enter unicode values I think

---

### Post by Golem XIV on 2008-01-10
I think that both the Spanish and the Latin American keyboard layouts support accents as dead keys (i.e. ' + a = á, ' + e = é etc).   I have used this same system with US International layouts (with dead keys), both on Windows and in Ubuntu.  For me this is the fastest way of getting the accented characters.

---

### Post by notbitmonk on 2008-02-24
Reviewing the post somewhat late but thanks to all that replied.  I figured it out when volunteering to translate Gnome applications.  The reason to ask for this is because I write in Spanish too.  In Spanish we need characters like á, é, í, ó, ú, ñ, ü, ¡ and ¿.  This also helped to look for the same option in the MS Windows computer I use at work.

---

