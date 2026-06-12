---
title: "Why is my KDE so Gnomy?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by Amablue on 2007-07-20
I installed kde-core so that I could play around with KDE to see if I like it more, but there's some style issues that are bugging me. For example, when I open up a save prompt, it looks like it's trying to be GNOME.

I'm sure it's not supposed to be like that, how do I get it to the way it should be?

---

### Post by luctor on 2007-07-20
If you want a fully fledged KDE Desktop, it's best to install kubuntu-desktop.
Be aware that this will turn your Ubuntu in Kubuntu, but it gives you a full kde

---

### Post by luisromangz on 2007-07-20
Well, what is happening is that you are using firefox, which is a GTK app, so its dialogs are GTK dialogs (which GNOME apps also use), so it's not actually a gnomy look-and-feel but a gtky one. So it is supossed to look that way, although you can change the style of GTK apps under KDE in KControl, by installing the gtk-qt package.

You can even use a style which will look the same in Qt and GTK apps, which is called QtCurve (look for it in kde-look.org). 

But GTK dialogs will always be different from Qt dialogs, as they are different toolkits.

---

