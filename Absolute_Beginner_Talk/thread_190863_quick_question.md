---
title: "quick question"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by highslime on 2006-06-06
I've seen in several screenshots of desktops that some of you guys have your windows partition available to you as an icon on the desktop.  I was wondering if someone could help me out with that.  I tried making a shortcut from the system:/media folder(like you can do in windows), but it then tried to copy my entire partition to it.  I cancelled that out, and when I did, it locked up and I reset.  It was nifty how it asked me I wanted to restore my session, a very convenient feature.  How is that done by the way, is it because of the ext3(journaling) filesystem?  But yeah, a lil how-to to make my windows partition available to me on the desktop would be greatly appreciated.  :mrgreen: :mrgreen:

---

### Post by rado_london on 2006-06-06
Quick answer. Go to Applications-System tools- Configuration Editor. In it go to apps-nautilus-desktop and tick volumes_visible.

---

### Post by highslime on 2006-06-06
thanks. just one thing. i'm using kde, i don't see that path, but i'm sure it's here.. somewhere.

---

### Post by rado_london on 2006-06-06
Hold on
That was for GNOME. SOrry I didnt know u have KDE. I dont have and idea about KDE though. You can try to go to Computer and Drag the icon and it will ask you if you want to link it. At least in SUSE 10 was that way.

---

### Post by highslime on 2006-06-06
Wewt. Problem solved.  I read somewhere there's a kcontrol command you use in the console, takes you to the KDE Control Center.  From there go to Desktop>Behavior>Device Icon tab>make sure mounted hard disk volume is checked, and it throws up the icons for the drives i need.  most excellent.  now to figure out how to add this to the K menu :D

EDIT: lol i'm a dork.  just go to system settings on the Kmenu>Display... i could have sworn the device icon tab wasn't there a bit ago....

---

