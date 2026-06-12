---
title: "Wine Menu in GNOME"
date: 2006-08-27
forum: Absolute Beginner Talk
---

### Post by SonicChao on 2006-08-27
I use a program that runs in Wine a lot, and it always crashes when I:

```

wine ~/.wine/LiveSwif 2.2/liveswif.exe

```

But in KDE, there was a Wine menu in the KMenu. It didn't crash 9/10 times when launched from KDE's menu. How can I get a menu like that in GNOME? I looked through Alcarte Menu Editor, turned on Debian menu and such, but still don't see a Wine menu. :(

---

### Post by bodhi.zazen on 2006-08-27
Don't know about menu in Gnome.

As far as crashing, try changing

wine ~/.wine/LiveSwif 2.2/liveswif.exe

to

wine /home/user_name/.wine/LiveSwif 2.2/liveswif.exe

or

wine /home/user_name/.wine/LiveSwif\ 2.2/liveswif.exe

---

### Post by SonicChao on 2006-08-27
Thanks for the reply, but both of those caused it to crash...

I think that the shortcut in the Menu is the program with all the other exe's working at the same time? Not so sure because I don't know much about Wine. Just that this works in KDE and doesn't in Gnome.

---

### Post by SonicChao on 2006-08-27
*bump*

---

### Post by DoctorMO on 2006-11-11
try winelauncher instead, this uses the configuration from winecfg and is the thing both gnome and kde use to launch wine things.

---

### Post by g4c9z on 2006-11-29
> **SonicChao said:**
> How can I get a menu like that in GNOME? I looked through Alcarte Menu Editor, turned on Debian menu and such, but still don't see a Wine menu. :(

You can make the menu item yourself.  Find out what command the KDE menu item is using (right-click the KDE menu, "menu editor", check the menu item for the command it uses), then go to the Alcarte Menu Editor, create a new item, and for the command enter the same command that the KDE menu item had.

Not all programs you install go on the Gnome and KDE menus automatically.  It's normally only graphical programs that get put there automatically (wine is a command-line program, I think) and maybe not even all of those, but I'm not sure.

---

