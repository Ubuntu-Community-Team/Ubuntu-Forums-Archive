---
title: "Playing Steam Games in Wine"
date: 2007-09-02
forum: Absolute Beginner Talk
---

### Post by nar57981 on 2007-09-02
I'm not that technical with linux, but I found some easy ways and guides to install things like Compiz Fusion and Wine. I got steam to install on wine, and everything works. But, while playing a game like CS 1.6 the menu bars cover up my health and ammo counters.

Am I going to have to manually say to hide the menu bars every time, or is there some kind of script that when my game starts, it'll hide the bars for me?

Sorry if this is already answered somewhere, or is really noob-ish!

Thanks for the reply

---

### Post by dfreer on 2007-09-02
Try going into winecfg, and try selecting "Allow window manager to Control Windows". You may also want to try turning off Compiz Fusion to see if that makes a difference. Also, which version of wine are you running?
```
wine --version
```
If you are running an older version, the solution just may be to install a newer package ;)

---

### Post by nar57981 on 2007-09-02
Alright, I had the window manger, managing. And my version is 0.9.33. If it's a problem with my version, could you tell me the code to update it? Or would I have to completely uninstall it?

Also this is going to sound really bad...but how do I turn off my Compiz Fusion? To turn it on I saw somewhere that I go into ALT+F2 and I typed in "compiz --replace". And it started working.

Thanks for all the help, and sorry if it's a little remedial!

---

### Post by dfreer on 2007-09-02
Hmmm... I generally use the fusion-icon in my systray to change from using compiz - metacity, I believe this command will also work with ALT+F2:
```
metacity --replace
```
Wine is on version 9.44 as of this writing, the problem you are experiencing may very well be fixed in the newer version, and you may not need to switch back to metacity. Wine has it's own repository that will almost always have the latest wine version in it, if you wish you can add the repository by following these instructions:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Hopefully this will help fix things. I'm pretty sure the top-bottom bar overlap was a bug that existed in the early 9.3X versions and may not have anything to do with compiz fusion.

---

