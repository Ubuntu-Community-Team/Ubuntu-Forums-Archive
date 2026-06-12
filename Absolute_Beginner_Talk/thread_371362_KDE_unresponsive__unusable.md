---
title: "KDE unresponsive / unusable"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by c3007223 on 2007-02-26
Hello, I have been using Linux (Ubuntu 6.06) for about one month, and am new to forums, so please bare with me.

I installed Ubuntu 6.06, on my Dell Inspirion 510m. Everything worked fine. I then installed KDE using aptitude as outlined on this site [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde). Everything was working fine, I could switch between either desktop managers, fiddle with the desktop settings, no problems. 

Three days ago I hit the default button in the KDE system settings menu. The computer became unresponsive, while I though the changes were being made. After twenty minutes the computer was still unresponsive, so I rebooted. Now every time I log into KDE, the computer becomes extremely sluggish, taking at least 5 minutes to load the desktop. A windw appears in which it says that trash files are being checked, and has a progress bar. After 2-3 minutes,with no progress shown, the window disappears. The system places menu appears as 'empty', and the system settings and Konqueror windows show nothing. Firefox still works, but the whole performance of the system remains very slow.

When I log into Gnome, the computer works perfectly.

I tried to remove KDE and reinstall it as outlined at [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde), though the problem remains.

Any suggestions would be greatly appreciated.

---

### Post by ed-j on 2007-02-26
Caution: Reply from Novice!

If you have a low spec' computer, the default settings in KDE may be too much for it? Have you successfully uninstalled?

Best I can do!

---

### Post by sardion on 2007-02-26
Boot into gnome and do this in terminal:

rm -fr ~/.kde

That wil lremove all your kde settings.  Then if you switch to KDE it will be like the first time.  Don't hit the default button this time around I guess (no idea why that caused this).

---

### Post by c3007223 on 2007-02-26
I have a Dell Inspirion 510m, 1.8 GHz Pentium M Centrino Processor, 512 MB ram, I dunno what other hardware specifications are relevant, though I bought it two years ago, and as such I assume it is fine to run KDE, anyhow, wouldn't have I been using the default settings when I first installed KDE? It ran perfectly then. In any case, the settings application in KDE shows a blank window, so I cannot change anything.

The uninstall of KDE went without problems, as did the reinstall, though the same problem persists.

Cheers.

---

### Post by c3007223 on 2007-02-26
> **sardion said:**
> Boot into gnome and do this in terminal:

rm -fr ~/.kde

That wil lremove all your kde settings.  Then if you switch to KDE it will be like the first time.  Don't hit the default button this time around I guess (no idea why that caused this).

Mate, that worked perfectly, Thank you very much.

---

