---
title: "Problems logging in with 8.10 runnung in Paralles VM (Mac OS X)"
date: 2008-12-12
forum: Apple Hardware Users
---

### Post by GammaQuantum on 2008-12-12
Hi everyone,

I downloaded Kubuntu 8.10 and installed it in a virtual machine in Mac OS X. It emulates a core 2 duo processor, it has 1 GiB of RAM and no special graphics card.

It starts up normally, as far as I can tell. Then I get the loggon screen, type in name and password and get the "progress bar", with the five icons fading in. I see the KDE screen for a second, and then I get console and the loggon screen again. I made a screenshot where you can see that bit of KDE, I can see before it goes to console and back to log in.

[http://img145.imageshack.us/my.php?image=picpd3.jpg](http://img145.imageshack.us/my.php?image=picpd3.jpg)

Has this something to do with the X Server or a missing special graphics card or so? It seems to me, that the X Server gets restartet and then I am "logged out".

I just tired to boot from my older regular Ubuntu 6.10 CD, it worked pretty good, I did not have the same error. So is it the new Version of the X Server, or just KDE instead of Gnome?

I would appreciate all comments and Ideas,

GammaQuantum

---

### Post by Leslie Viljoen on 2008-12-12
Your Xorg log file (/var/log/Xorg.0.log) might shed some light on the situation. 
From the console:
> egrep '^\(EE|^\(WW' /var/log/Xorg.0.log
This command will search for lines starting with (EE or (WW, indicating errors or warnings. Can you post the result?

---

### Post by GammaQuantum on 2008-12-13
I cannot type or copy the string, because my keyboard layout does not work too well (I got a german keyboard).

I downloaded Kubuntu 8.4 from the Parallels webpage and it works pretty good. Could it be that there is a different graphics driver or so, that does not work with Parallels yet?

---

### Post by cyberdork33 on 2008-12-13
8.10 doesn't work well in parallels < 4.0

---

### Post by GammaQuantum on 2008-12-14
You got to be kidding me, I just bought Parallels two weeks ago and I got Version 3. And now they got Version 4...

I don't really want to spend 30€ on an upgrade, so I guess I have to stick with the older Kubuntu version.

Okay, thank you all!

---

### Post by cyberdork33 on 2008-12-15
> **GammaQuantum said:**
> You got to be kidding me, I just bought Parallels two weeks ago and I got Version 3. And now they got Version 4...

I don't really want to spend 30&#8364; on an upgrade, so I guess I have to stick with the older Kubuntu version.

Okay, thank you all!
All purchases since Sept 1 qualify for a free upgrade.
[http://www.parallels.com/support/pdfm4-upgrade-key/](http://www.parallels.com/support/pdfm4-upgrade-key/)

---

### Post by GammaQuantum on 2008-12-15
Let me give you a million thank you:

[http://www.who-cares.ch/inhalt/1000000-thank-you.html](http://www.who-cares.ch/inhalt/1000000-thank-you.html)

---

### Post by GammaQuantum on 2008-12-16
I just downloaded Parallels 4 and installed it. It took like 10 seconds to convert this Ubuntu 8.10 Installation and it runs pretty good now, stable but just a little slow. But that has to be some kind of Parallels problem, maybe with the graphics card.

My first impression of KDE 4 just was "wow!" It looks really cool with the glass effects and the nice wallpaper. I like it very much.

And on the second screen Parallels is converting my windows, which already told me "that my hardware significantly changed and I have to re-active it". One + for Linux again ;)

GammaQuantum

---

