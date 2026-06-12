---
title: "Weirdo-Looking sessions menu. How can I fix??"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by vasiliymeshko on 2007-07-06
Ok, what I'm talking about is the sessions menu on the KDM login prompt, to change between KDE, GNOME, etc. Normally mine is supposed to look like this:
&#1058;&#1080;&#1087;&#1086;&#1074;&#1080;&#1081; *(Default)*
FVWM
FVWM-Crystal
GNOME
KDE
Wmii
XFCE Session
&#1041;&#1077;&#1079;&#1087;&#1077;&#1095;&#1085;&#1080;&#1081; *(Failsafe)*

Now, (after my last update, seems like) it looks like this:

&#1058;&#1080;&#1087;&#1086;&#1074;&#1080;&#1081;
FVWM
FVWM-Crystal
**Fvwm**  *[COLOR="Green"] <-- //Help! How do I get rid of these[/COLOR]*
GNOME
KDE
**Metacity** *[COLOR="Green"][I]<--*[/COLOR][/I]
Wmii
**Wmii** [COLOR="Green"]*<--*[/COLOR]
**XFwm** [COLOR="Green"]*<--*[/COLOR]
XFCE Session
&#1041;&#1077;&#1079;&#1087;&#1077;&#1095;&#1085;&#1080;&#1081;

Does anyone know what's going on here, and how to fix this? Big thanks in advance.

---

### Post by iDid on 2007-07-06
hello

you might try to type a
sudo dpkg-reconfigure kdm in your konsole
and choose kdm again then validate...

Hope this will help!

---

### Post by vasiliymeshko on 2007-07-06
```
sudo dpkg-reconfigure kdm
```
Unfortunately that did not fix it.
Now, I've also tried selecting GDM to see what happens. There, the menu looks normal. It's when using KDM, I get all those extra options.

---

### Post by iDid on 2007-07-07
What happens if you create a new user and login with this user?

---

### Post by vasiliymeshko on 2007-07-30
Haven't had much time to look at it for a while, but no, creating new users does not seem to work either. 

I've noticed that Adept includes the following description for the KDM package:

"The menu package will help to provide KDM with a list of window managers that can be launched, if the window manager does not register with KDM already. Most users won't need this."

I do have the menu package installed, so looks like it just might be what's cusing the problem. Anyone knows how to workaround this. Would removing the menu package fix it? And would I loose the Debian menu if I do remove it (don't want to).

---

### Post by vasiliymeshko on 2007-08-01
bump

---

