---
title: "1 week linux user! wine or cedega?"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by Jainor on 2006-01-28
i need to get WINE working period. and do i need to get cedega? i'm not a hardcore graphics gamer i like more stradegy games and the like. but before any of that happens i need to get my wine working and my Wireless PCI adapter to work. please send advice! i need help getting started. i've had Linux for a week and i'm struggling.

---

### Post by moephan on 2006-01-28
You would only need Cedega if your games didn't work with Wine. Cegega is basically wine with a laser like focus on supporting games.

---

### Post by mgmiller on 2006-01-29
If you want to get the newest most up to date wine, you should get it straight from the winehq.  Here's how to add them to your repositories:

First, back up your old repository list:
sudo cp /etc/apt/sources.list /etc/apt/sources.backup

Next, edit your sources list:
sudo gedit /etc/apt/sources.list

In the opened file, add the following 3 lines to the bottom:
## The wine sources
deb [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) binary/
deb-src [http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) source/

Click save and then close the file.

go to your synaptic package manager (System>Administration>Synaptic Package Manager)

and click on reload to add the new repositories to your acitve list.  (You may have to click on reload twice).

Finally, click on search and search for wine.
You only need to install the single entry called wine.  The current one is 0.9.6-winehq-1.   

After it's installed, you configure it by holding down the ALT key and tap the F2 key.  In the resulting dialog box that opens, at the top type winecfg

You should read more at the wine headquarters  [http://www.winehq.org/](http://www.winehq.org/)

I have several windows apps running this way including dvdshrink, and they work fine.

Good luck.

---

