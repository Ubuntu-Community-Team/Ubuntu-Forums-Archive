---
title: "Dapper and Japanese keyboard on ibookG4"
date: 2006-08-27
forum: Apple PPC Users
---

### Post by boccaccio on 2006-08-27
Hi, I have an ibook G4 with a japanese keyboard and dapper ubuntu installed in it.

I have a problem: I cannot have a proper setup for the keyboard.

From System->Preferences->Keyboard,

if I choose a Japanese Layout, then i write only in katakana (i.e. japanese characters), [nothing to do with scim, i keep it off]

if I choose the layout: Japan (PC-98xx Series), with Japanese 106 keys, I get latin characters, qwerty..., BUT i do not have a way to press two characters: a blackslash and a vertical bar.

A way out is to completely change the layout into an english one. but of course it is a little bit ridiculous.

Does anybody know how to fix all these?

Cheers,
-- Antonio

---

### Post by didg on 2006-08-27
IMO the easiest:

In Keyboard Layouts Preferences tab:
1) use Macintosh keyboard model
2) select your default layout, i.e. Japanese layout.
3) add a second layout qwerty

In Keyboard Layouts Options tab:
play with Alt/Win key behavior
I'm using shift+shift for changing group and press right logo (right Apple key) .

Now you get vertical bar with <shift> <right Apple key> <key from qwerty layout> 

Another option is to add them with xmodmap but it's a pain with upgrade, when you change computer and so on.

---

