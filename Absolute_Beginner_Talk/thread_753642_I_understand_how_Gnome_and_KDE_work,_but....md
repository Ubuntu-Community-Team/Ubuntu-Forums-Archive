---
title: "I understand how Gnome and KDE work, but..."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Exershio on 2008-04-12
I understand that Gnome uses GTK and KDE uses QT, but what do the other window managers use (like fluxbox, icewm, e17, etc)

Or if I'm misunderstanding something, feel free to correct me. I'd appreciate it.

---

### Post by The Titan on 2008-04-12
> **Exershio said:**
> I understand that Gnome uses GTK and KDE uses QT, but what do the other window managers use (like fluxbox, icewm, e17, etc)

Or if I'm misunderstanding something, feel free to correct me. I'd appreciate it.
I'm not sure but i think that Gnome is like a "base" for other window managers.  Like gnome cant run without a window manager and vice versa.  I could be way off about this but that is my understanding.

---

### Post by PeterJS on 2008-04-12
The window managers themselves don't use anything. You can use any window manager with any application. Other than the fact it would look kind of funny and be hard to configure, you could use Kwin with gnome-panel, and the other GTK apps that commonly make up the Gnome desktop. Conversely you could use Metacity with Kicker and the QT apps that commonly make up KDE. If you wanted to do something really weird you could run kicker, with GTK apps, and e17 as the window manager. It's the applications that use the tool kits, the only reason that the tool kits are associated with the desktop environments is that running a mixed environment looks really funny, so it's best to only use only applications from one tool kit, Gnome defaulted to GTK, and KDE defaults to QT.

There are other tool kits out there for example VLC use WXwindows.  E17, is trying hard to push the EFL (enlightenment foundation libraries), but they still use a lot of GTK. One of the earlier versions of enlightenment (e15?) was the window manager for Gnome back in the 1.x era.

---

### Post by fredbird67 on 2008-04-12
I know that Xfce, Openbox, and LXDE all use GTK, and I wouldn't be surprised if there are others.  However, I don't know of anything right offhand other than KDE that use Qt, but again, I wouldn't be surprised if there are others using Qt, too.

Fred in St. Louis

---

### Post by smartboyathome on 2008-04-14
E17 now uses ETK, which is based off of EFL.

---

### Post by SunnyRabbiera on 2008-04-14
most of the time I see others use GTK, as it seems to be very common in other window managers/DE's
XFCE and LXDE are both very GTK dependent

---

