---
title: "Compiz/Beryl (un)install problems"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Servaas on 2006-11-18
Hey,

Recently I tried to install Compiz, I followed a guide somewhere on this forum for nvidia cards with the beta drivers. After some apt-gets it was installed but I couldn't get it to run, tried to do it in terminal with "compiz --replace --use-conf gconf" but I got "Compiz: no composite extension". Any other command starting with compiz gave that error. I looked it up and it's got to do something with AIGLX or something but afaik it should use the nvidia beta driver's because those have integrated aiglx, right? I tried adding "Composite" "True" to the config but then I just got a screen with a flurry of colours, had to reach for the power button. Tried Beryl but that gave the exact same error. So then I tried deinstalling it by removing the packages from synapsis (sp) but now my gnome won't boot anymore. It's just stuck at "Loading window manager" even though I selected GNOME/ "Default system session" as session. I tried loading fail-safe gnome session and that works but I can't do much in that one, also the headers of every screen are gone. I mean the thing at the top where you have to click to drag them. I tried using "metacity --replace" and that fixed it, but only temporarly, I could add it to Sessions I guess but I don't like path solutions, and I'm still stuck in that failsafe session anyway.

Somehow, somewhere a terminal with a gnome log popped up and apparently it's still trying to load compiz even though it's not the compiz session, and compiz packages are deinstalled. Unfortunately I can't get that log to show up anymore. Any thoughts? Tried reinstalling gnome but there's so many packages starting with gnome I'm not sure which one to select. I would just like to have a working gnome back for now.

edit: Using Ubuntu Dapper.

---

### Post by ThrobbingBrain66 on 2006-11-18
I had a similar issue when I first started using Ubuntu back in April.  I thought that the boot process stuck at Loading Window Manager too, but it actually just took a REALLY long time to load...5-6 minutes if I remember correctly, maybe a bit longer

First I would suggest that you try to boot to your regular installation first.  But when it looks like its frozen, just give it some time.  If you do get in that way, then you can make sure that all compiz packages are removed, revert back to your old xorg.conf (you did make a backup, right?), take compiz out of the startup programs and finally reinstall metacity (if necessary).

```
sudo aptitude remove --purge compiz*
```
i think all compiz packages start with compiz-XXXXXX, so that should get rid of any straglers

```
sudo aptitude install metacity
```
will reinstall metacity

as for restoring a backup of your xorg.conf, if you didnt make one yourself, i believe theres a backup made by default anyway.  You'll have to open up the folder and look for it.  its named xorg.conf.xxxxxxxxxxxxxx (x's indicate the date plus some other numbers.)

---

### Post by PriceChild on 2006-11-18
```
sudo dpkg-reconfigure xserver-xorg --phigh
```Should remake your xorg.conf asking you as little questions as possible. (there might only be one - before the phigh...)

---

### Post by Servaas on 2006-11-18
I did the following:
- Removed all packages with compiz in the name
- Reinstalled metacity
- Put back my xorg.conf backup
- Generated a new one with the command above
- Checked Sessions -> Auto execute on boot for compiz entries, but nothing showed.

None really helped. It's still stuck on Loading window manager but it does load after 2-3 minutes. No window decoration though. It's not stuck on loading windows manager anymore if I reinstall Compiz, but no window decoration, let stand a working Compiz. Should I just install another windows manager like KDE or reinstall ubuntu?

Similar problem [here](http://www.ubuntuforums.org/showthread.php?t=301215&highlight=compiz). I'm going to try the gnome-settings-daemon & command now, perhaps that'll work.

edit: "You can only run one xsettings manager at a time; exiting".
edit2: Just wondering, is it normal that I have a xserver-xorg-driver-ati installed even though I have a nvidia card?

---

