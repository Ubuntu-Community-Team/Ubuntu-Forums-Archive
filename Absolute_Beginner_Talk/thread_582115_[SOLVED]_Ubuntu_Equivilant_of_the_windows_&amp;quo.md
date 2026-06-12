---
title: "[SOLVED] Ubuntu Equivilant of the windows &amp;quot;Start &amp;gt; Startup&amp;quot; folder?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-10-19
Everyone who's used windows knows about the startup folder - everything in it is launched in startup.  There are also scheduled tasks that can run on logon, but you get the point.

Is there a Ubuntu equivalent of this folder?  I know I can add startup tasks using the System > Preferences > Session menu, but I need rather A) a command to add a start-up task, or B) the location of (if there is such a thing) the file/folder that stores what is to be run on start-up

Anyone know?...

---

### Post by loganm10 on 2007-10-19
the folder where the startup links is held is:

~/.config/autostart

the ~ is the name of the user it works out to:

/home/logan/.config/autostart for me

this folder contains files, not actual programs, not even links, but files that are just plain text, they look like this:

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=No Name
Type=Application
Name[en_CA]=compiz
Exec=compiz --replace
X-GNOME-Autostart-enabled=true
GenericName[en_CA]=

that is one of mine anyway

---

### Post by loganm10 on 2007-10-19
also that folder might not exist if you havent added anything to the Preferences>Sessions, but you can just create it

---

### Post by ryanVickers on 2007-10-19
thanks ;)

---

