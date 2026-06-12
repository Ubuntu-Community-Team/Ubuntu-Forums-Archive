---
title: "Firefox Broken"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by JcZndeR on 2006-08-08
As you can tell by the thread name by Firefox Web Browser is broken.
I was updating it from Mozilla Firefox 1.5.0.4 to 1.5.0.6 via the internal updater using the command "gksudo firefox", which I saw from another thread.  After Firefox never started again.  Now I am using Opera for the moment but I happen to like Firefox better and I need it for Script testing...  Since it didn't work I uninstalled it following the instructions from [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion), which I originally installed it from.  Then I reinstalled which still didn't work so I uninstalled it again and moved my user's folder "********.default"; after I deleted the /opt/firefox and ~/.mozilla/firefox, also deleted the firefox launchers in usr/bin/.
When I installed it failed to start yet again and when I run the "firefox" in the terminal it says > /opt/firefox/run-mozilla.sh: line 131: **** Segmentation fault      "$prog" ${1+"$@"}
Where "****" is a seemingly random string of numbers (e.g. 6412).

Maybe the newest firefox version is broken?  I redownloaded the package twice so the file isn't corrupt.  I guess it could be that those instructions just don't work on this new package, Or maybe I screwed something up using "gksudo firefox".  At this point I can't really tell.  Opera is running really slow when it comes to loading webpages so I am really hoping someone can help me out here.  Thanks!

Edit:  Yeah I was going to say that I am not using my ubuntu computer right not because of Opera being slow and all, so I hand typed the error and it might be wrong but its somewhere along those lines.  (The Opera problem may just be my internet right now.)

---

### Post by orb9220 on 2006-08-08
gksudo firefox dosn't update that is graphical-sudo firefox runs the program.

---

### Post by JcZndeR on 2006-08-08
> **orb9220 said:**
> gksudo firefox dosn't update that is graphical-sudo firefox runs the program.

LOL...
Yes I realize that, I just didn't mention it in the post.
However that doesn't change the fact that I can't run the program either way. :sad:

---

