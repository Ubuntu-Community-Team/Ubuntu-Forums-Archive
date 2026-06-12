---
title: "Gnome apps fugly in KDE"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by alex-desktop79 on 2007-04-01
I did
> sudo apt-get install kde-core
Worked very nicely! Except all my gnome applications are fugly in KDE.
And this is the second time I try to post this, firefox crashed the first.
[img]http://img47.imageshack.us/img47/3199/screenshotpe7.png[/img]
Notice the Close button that is from an application that was installed in gnome, and the other two buttons, they are from an app that came with KDE.

---

### Post by Big Dave on 2007-04-01
Gnome is written using GTK+ whereas KDE is written using the Qt toolkit. The two look different, and the only way to minimise that effect is to use a theme where the two look very similar.

---

### Post by alex-desktop79 on 2007-04-01
So it's normal? Even firefox is ugly.

---

### Post by rillip on 2007-04-01
Firefox shouldn't be affected either way; it's not a Gnome or KDE app.  You'll just have to play with it to make it look the way you like.

As for Gnome apps looking ugly in KDE... it's Gnome.  They probably look good in Gnome.  But KDE != Gnome.  Your options, as I see it, are as follows:

Use Gnome instead of KDE
Use KDE apps instead of Gnome ones
Change your theme as Big Dave suggested (best of luck with that)

It's kind of like trying to put a pick up truck's dash in a sport's car's frame... you might make it work, but it's not going to be pretty.

---

### Post by alex-desktop79 on 2007-04-01
What I mean to say is **anything** that was installed in gnome is really ugly in KDE, even firefox and beryl-settings. All of them.

---

### Post by nixclusive on 2007-04-01
Well most of the time its only the cosmetic changes. The programs' functionality is largely remains unaffected.

---

### Post by Bachstelze on 2007-04-01
```
sudo apt-get install gtk-theme-switch
```

then in a terminal

```
gtk-theme-switch2
```

and choose the theme of your choice.

---

### Post by finferflu on 2007-04-01
Just DON'T use the gtk-qt-engine. I did in the past, it's buggy and will slow down your system miserably. I just told you in case you found out that kind of soultion in the future. Just be kind to yourself, and don't install that kind of stuff.

---

### Post by Bachstelze on 2007-04-01
Agreed. I always use the Clearlooks GTK theme and it integrates fairly well mith my KDE theme (usually Plastik).

---

### Post by luisromangz on 2007-04-01
It is not a problem with Gnome apps, it's a problem with all GTK apps, that's the reason Firefox also looks ugly. What you should do is to install a package called gtk2-engines-gtk-qt. This GTK theme engine provides a way to select GTK app's theme from KDE Control Center. There you can select the theme you want for those apps.

If you want all apps (GTK and Qt ones) looking the same way, you should install the QtCurve theme, which can be found in [http://www.kde-look.org]("http://www.kde-look.org") or in some repositories, like Treviño's. I use it and I'm so happy of having a very good looking and consistent graphical user interface.

Good luck!

---

### Post by alex-desktop79 on 2007-04-01
> Code:

sudo apt-get install gtk-theme-switch

then in a terminal

Code:

gtk-theme-switch2

and choose the theme of your choice.
Thanks! Works like a charm

---

