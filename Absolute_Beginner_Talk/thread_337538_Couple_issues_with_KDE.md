---
title: "Couple issues with KDE"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by kilou on 2007-01-13
Hi,

I've been using Gnome on Edgy for a while and like it but I now want to switch t KDE because it has more options and seems to run Beryl smoother (on my system...). I made a clean install of Kubuntu and I try to set it up properly now but face some issues:

1) How to make beryl and emerald start on startup? Gnome had a GUI to change startup programs but I can't find the same in KDE. I can start beryl with a symlink in /.kde/autostart folder but I also need to start "emerald --replace" to avoid missing borders on windows. Is there a GUI where I can change the startup program options in KDE?

2) Problem with file association: in a email (thunderbird) when I click on an attached PDF file, KDE proposes KGhostView as viewer. However when I look at the file association, PDF is first associated with KPDF and then with KGhostView. I tried to remove KGhostView from the association to PDF file but PDF are always opened with KGhostView when they are attached in a mail. Is there a way to use KPDF as the default viewer of PDF files??

3) How can I set the root password in KDE??? I also cannot find this while it was easy in Gnome...

certainly more to come...

Thanks

---

### Post by ajmorris on 2007-01-13
> **kilou said:**
> Hi,

1) How to make beryl and emerald start on startup? Gnome had a GUI to change startup programs but I can't find the same in KDE. I can start beryl with a symlink in /.kde/autostart folder but I also need to start "emerald --replace" to avoid missing borders on windows. Is there a GUI where I can change the startup program options in KDE?

press alt+F2 and type "kcontrol" in there is a configuration for startup items. I can't remember where exaclty as i haven't used kde in a while, but it is there.

> 2) Problem with file association: in a email (thunderbird) when I click on an attached PDF file, KDE proposes KGhostView as viewer. However when I look at the file association, PDF is first associated with KPDF and then with KGhostView. I tried to remove KGhostView from the association to PDF file but PDF are always opened with KGhostView when they are attached in a mail. Is there a way to use KPDF as the default viewer of PDF files??

Thunderbird probably has it's own config. I think in the attatchments tab in preference you can set what file types are opened with what application.

> 3) How can I set the root password in KDE??? I also cannot find this while it was easy in Gnome... unfortunately for this one i don't know.

---

### Post by kilou on 2007-01-13
Thanks for your help. Unfortunately I couldn't find any startup manager in kcontrol. There is something about session manager or service manager but none seem to contain software that loads on startup. so that I can add beryl and emerald :( 

some other problems:

4) After logging out (choose "end current session") and logging in back on the same account, I loose the desktop background and cannot access some folders (on a media drive)! If I restart the computer the background is back and access is OK too. Any clue?

5)  When adding a bookmark to a folder in Konqueror (file browser), the bookmark is not available as a location when saving a file. This worked in Gnome with Nautilus but I cannot get it to work in KDE.

---

### Post by ajmorris on 2007-01-13
> **kilou said:**
> Thanks for your help. Unfortunately I couldn't find any startup manager in kcontrol. There is something about session manager or service manager but none seem to contain software that loads on startup. so that I can add beryl and emerald :( 


It is called session manager i believe. but when running KDE any application that is running when you shutdown will start again when you boot up. Just have both beryl and emerald manager open when you shutdown.

---

### Post by ajmorris on 2007-01-13
> **kilou said:**
> Thanks for your help. Unfortunately I couldn't find any startup manager in kcontrol. There is something about session manager or service manager but none seem to contain software that loads on startup. so that I can add beryl and emerald :( 


It is called session manager i believe. but when running KDE any application that is running when you shutdown will start again when you boot up. Just have both beryl and emerald manager open when you shutdown.

for 3) and 4) sorry i don't know.

---

### Post by ajmorris on 2007-01-13
lol... whoops double post.

---

