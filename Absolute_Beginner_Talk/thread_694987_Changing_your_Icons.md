---
title: "Changing your Icons"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-02-12
Hello
I have a bit of a problem i got a full icon package for Example this one..
[http://www.gnome-look.org/content/show.php/Oxygen-Refit?content=74900](http://www.gnome-look.org/content/show.php/Oxygen-Refit?content=74900)

when i apply it.  Only the desktop icons changes nothing else none of the Application icons change at all, how do i make the Application icons change?

---

### Post by Bluestick on 2008-02-12
when i do extract the package it does come with all the system "application" icons so i know it has it just not applied on my PC :(

---

### Post by klemens on 2008-02-12
wich icons do you mean,
the desktop icons change that's what it is.

for example firefox buttons can be changed by downloading a theme.
the rest is the theme manager of gnome/kde whatever you use.

so don't see what you mean.

---

### Post by stchman on 2008-02-12
> **Bluestick said:**
> Hello
I have a bit of a problem i got a full icon package for Example this one..
[http://www.gnome-look.org/content/show.php/Oxygen-Refit?content=74900](http://www.gnome-look.org/content/show.php/Oxygen-Refit?content=74900)

when i apply it.  Only the desktop icons changes nothing else none of the Application icons change at all, how do i make the Application icons change?

They should change automatically.  Did you install them via the Themes Manager.  If yes then select them in the Icons tab when you hit Customize.

---

### Post by Bluestick on 2008-02-12
ok i do have via desktop and all the other stuff installed emerald and so on...

 i mean this icons.. check out the screenshot

---

### Post by klemens on 2008-02-12
as far as i know they use the program icon and can't be changed in the menu.

could get kinda hard to change those.

---

### Post by jordanmthomas on 2008-02-12
If a theme doesn't change an application's icon, it's because the author of the theme didn't write a rule to change it.

You'll find that most gnome icon themes will not change any KDE program icons.

Your screenshot shows expected behavior.  It shouldn't be necessary, but to guarantee the panel reloads its icons, you can run
```
killall gnome-panel
``` and it will restart itself.  Chances are, the icons will still be the same though.


edit:  I hadn't actually looked at your theme at gnome-look:  it seems you haven't applied the theme correctly

---

### Post by Bluestick on 2008-02-12
ok thx for the help u guys...

---

### Post by Therion on 2008-02-12
The website gives you instructions on how to update/change the icons once you've downloaded the file.  If I read them correctly, uou'll need to open a terminal, and go to the theme folder:

```
cd ~/.icons/Oxygen-Refit
```

and then run the commands as described on the webpage.  After that, go to the  Appearance menu,  and select the Oxygen-Refit icon theme.

---

