---
title: "Confused by difference between KDE and GDE with apps"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by comfortablynumb on 2006-09-07
New to Ubuntu, new to the forum 8) 

After searching through the forums, I got my system up and running 100% (nvida driver hell, then emu10K1 driver hell) but the thing that is stumping me is the difference between KDE and Gnome.

I originally installed Ubuntu 6.06, then I installed Kbuntu over it from Synaptic. I understand that some apps are written for each and they each have there following, but when I log into my Gnome interface I have all the KDE apps avaible,such as Amorak, Konversation and when I log into KDE I see Gnome apps. Are these apps cross compatible? 

Problem is, I think I like the Gnome interface over KDE, but it seems KDE has some better apps built for it such as
- IRC Client Konversation
- MP3/Audio Player Amorak
- DVD Playback Kaffeine

But then Gnome has a few things going for it, I prefer the 
-evolution email client over Konquest
-cleaner interface
-synaptic package manager

---

### Post by ahaslam on 2006-09-07
I'd read somewhere that your choice of DE may depend upon the app that you require (kde or gtk). Similar comments can easily be found on the web but are very misleading. You can run Qt ot Gtk apps in either kde or gnome without problems. Of course a Qt app will load slightly faster under Kde and vice versa for obvious reasons. The choice is a personal one, install mutiple sessions & find one that fits your needs.

Tony.

---

### Post by msandersen on 2006-09-07
The reason for the two Desktops are historical. KDE was the first Desktop Environment for Linux, but used the proprietary QT graphics library, so in 1997 the Gnome project was started using the GTK toolkit from The Gimp image editor (GTK = Gimp Tool Kit). Since then the license terms for QT has changed, though commercial developers still have to pay a few 1000 dollars for a single-user license, and the two projects have diverged further from each other. Recently they have coooperated more to make things work better across both, eg standardising where menus etc are stored.
A KDE app can still run in Gnome as long as the QT graphics library is installed, which it will be as a dependency, but it will take on the look of a KDE app. There are ways to match the themes.
For some light reading, try Wikipedia:
[http://en.wikipedia.org/wiki/KDE](http://en.wikipedia.org/wiki/KDE)
[http://en.wikipedia.org/wiki/GNOME](http://en.wikipedia.org/wiki/GNOME)

and if you just like Gnomes,
[http://en.wikipedia.org/wiki/Gnome](http://en.wikipedia.org/wiki/Gnome)

---

