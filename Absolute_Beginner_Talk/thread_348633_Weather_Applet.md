---
title: "Weather Applet"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Real Newbie on 2007-01-29
All,
My weather applet in the toobar has started showing a question mark for the last week. Anybody have any idea how to fix?

Thanks,
Noob

---

### Post by kanha on 2007-01-29
same problem here
i removed applet now:(

---

### Post by bapoumba on 2007-01-29
Hi,
right click on the applet, and either have a look at details, or update it. I get that when I boot my computer without network access. Once network is set up, it gets automatically updated every 30 mins (right click > Preferences), or I manually update it ;)

---

### Post by Real Newbie on 2007-01-29
I am on the network when I boot, I am on the network now. It is supposed to refresh every 30 minutes, but does not. When I click the update button nothing happens. I just keep the question mark in the tool bar.

Any ldeas?

Noob

---

### Post by MrKlean on 2007-01-29
never had the problem, but it sounds like it couldn't update for some reason.  I would remove it, and reinstall it, and set it up again.  BTW, that's one of my favorite things on Linux.  I have 2 setup for home and summer place ; )

---

### Post by Pobega on 2007-01-29
Which weather applet are you using? Adesklets? If it's adesklets, you might want to change the file's preferences in ~/.desklets/config.txt, although the exact file I am probably wrong on. You're best bet is to do ls ~/.desklets and figure out what the extension to the config file is yourself.

Or you could just do[quote]gedit ~/.desklets/config.*

---

### Post by Real Newbie on 2007-01-29
I am using the weather applett that is avaiable in the tool bar config menu. I am starting to believe that it ws broken during one of the updates that comes out. I tried reloading and no luck. If I am having trouble, surely there are others.

Anybody else having trouble with the weather applet?

Anybody tell me where I can get a different one that works?

Noob

---

### Post by ComplexNumber on 2007-01-29
> **Real Newbie said:**
> I am using the weather applett that is avaiable in the tool bar config menu. I am starting to believe that it ws broken during one of the updates that comes out. I tried reloading and no luck. If I am having trouble, surely there are others.

Anybody else having trouble with the weather applet?

Anybody tell me where I can get a different one that works?

Noobjust to eliminate the obvious, but have you selected the location correctly?  then update it.

its either that or it may well be that you have your firewall to be quite stringent. are you using a firewall frontend called firestarter?

---

### Post by Real Newbie on 2007-01-29
yep, nothing. I suppose that I need to report a problem.

Noobh

---

### Post by Hallvor on 2007-02-02
I have the same problem. Manual updates work fine, but it can`t update itself. I suspect it is a firewall issue.

---

### Post by psyne on 2007-02-02
I would just remove it and use the firefox extension it will popup weather information even when minimized and will not take space on your toolbar.

[http://forecastfox.mozdev.org/](http://forecastfox.mozdev.org/)

---

### Post by sbaker33 on 2007-02-03
Both new installations of Ubuntu 6.10 have this issue and from different networks.  One install that has been up and running since 6.10 was released is working.  All three were installed from different media.

---

### Post by Placenta Juan on 2007-03-01
Similar problem here. Everything is configured correctly and the weather applet updates itself like it should for about a day or two, then it blanks to a question mark and an "updating" message that never updates until I reboot or close the applet and add it to the taskbar again. Very annoying so I just removed it and added a weather plugin to gtkrellm.

---

### Post by sgstarling on 2007-03-01
I hope it gets fixed, it seems many enjoy it.

In the mean time, you may want to try my favorite: [weatherbug]("https://addons.mozilla.org/firefox/2455/") add-on for firefox.

---

