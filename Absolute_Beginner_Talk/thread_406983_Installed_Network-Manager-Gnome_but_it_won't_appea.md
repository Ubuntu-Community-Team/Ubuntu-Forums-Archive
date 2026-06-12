---
title: "Installed Network-Manager-Gnome but it won't appear in my system tray"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by Sporkmaster on 2007-04-11
I installed Network-Manager-Gnome but it's not appearing in my system tray, after 3 reboots and a reinstall. :( 

Is there some stupid little button I have to press or is it worse than that?

---

### Post by floke on 2007-04-11
You need the nm-applet - I think you can add it to the panel in the usual way (right click panel and select add to panel then search for the applet).

Be warned, it can give you problems. If its for wi-if then make sure you have wi-fi radar installed too in case network manager packs up on you.

---

### Post by freakavoid on 2007-04-11
Hi,

try adding this line to your startup programs (system->preferences->sessions)

```

nm-applet --sm-disable

```

---

### Post by Sporkmaster on 2007-04-11
> **Steve.K said:**
> You need the nm-applet - I think you can add it to the panel in the usual way (right click panel and select add to panel then search for the applet).

Be warned, it can give you problems. If its for wi-if then make sure you have wi-fi radar installed too in case network manager packs up on you.

There is no such applet in the add to panel menu - just the network monitor, which I already have up there

---

### Post by floke on 2007-04-11
Try running it from a terminal - just type 'nm-applet' and see what happened.
Can't remember exactly how to get it up since did mine a few days ago but have just got rid of it sinc ewas causing too many probs.

---

### Post by Sporkmaster on 2007-04-11
> **Steve.K said:**
> Try running it from a terminal - just type 'nm-applet' and see what happened.
Can't remember exactly how to get it up since did mine a few days ago but have just got rid of it sinc ewas causing too many probs.

Well, it's there now but I got "/bin/sh: /usr/bin/esd: not found" in the terminal and "connection information" is greyed out.

Also, I have no "Preferences menu" in Apps> System :confused:

---

### Post by floke on 2007-04-11
Yeah its a great app if you like headaches.
Have you tried editing the menu to see if you can get preferences back?
(right click on the menu icon and select edit menu).

---

### Post by Sporkmaster on 2007-04-11
I don't think there ever was a preferences button and I can't find how to get it...
There is no even slightly easier way to use wireless is there? :(

---

### Post by floke on 2007-04-11
Yep: wi-fi radar

sudo apt-get install wi-fi-radar

it'll go in the internet menu - just select the connection you want and away you go.

Have you tried right-clicking the menu icon to select edit menu?

---

### Post by cwmaxson on 2007-04-11
This one is better than wifi radar and network manager.  I would suggest it:

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

---

### Post by billygates on 2007-04-11
Mine went away once and with a lot of struggle, I found that the following brought it back.

Right click on the panel and select add to panel.

Then from the Utilities section, select Notification Area and click Add.

I know NOTHING about ubuntu,  But like I said, this worked for me and I was having a similar problem...

---

### Post by Sporkmaster on 2007-04-11
> **Steve.K said:**
> Yep: wi-fi radar

sudo apt-get install wi-fi-radar

it'll go in the internet menu - just select the connection you want and away you go.

Have you tried right-clicking the menu icon to select edit menu?

I right-clicked edit menu but found nothing like "Preferences," only "Settings"
After going off on an unrelated and pointless quest, (Ubuntu has some impressive screensavers) I got another wi-fi manager from Synaptec Package Manager... that code didn't work :( 

I'm about to reboot. Wish me luck.

---

### Post by floke on 2007-04-11
Oops, very sorry. the correct code is

sudo apt-get install wifi-radar

BTW: You don't have to reboot. You're not in Windows now :D

---

