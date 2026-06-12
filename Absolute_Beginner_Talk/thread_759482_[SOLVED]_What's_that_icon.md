---
title: "[SOLVED] What's that icon?"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by keymoo on 2008-04-19
Hi,

What's that icon next to firefox circled in red? [Click here (flickr)]("http://www.flickr.com/photos/markallison/2425184120/")


Thanks
keymoo

---

### Post by kerry_s on 2008-04-19
it's just a standard icon, what the app points to for it's icon.
you'll find it in different places, for example the displayed in your shot would be in /usr/share/applications/firefox.desktop
(i have iceape, so i'll use that as example), looks like this->
[Desktop Entry]
Encoding=UTF-8
Name=Iceape Suite
GenericName=Internet Suite
Exec=iceape %u
Terminal=false
Type=Application
Categories=GTK;Network
[B]Icon=iceape.xpm
[/B]

the icon for the menus is /usr/share/menus

---

### Post by meborc on 2008-04-19
this is the icon you click to get the window displayed on ALL workspaces, not only the one you are working on... try ticking it and then control+alt+right ... without ticking you would get just an empty workspace

some themes have it, some don't...

---

### Post by keymoo on 2008-04-19
Cool thanks!

---

