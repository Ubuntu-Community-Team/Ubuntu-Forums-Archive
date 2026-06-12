---
title: "how do i close an app from the terminal?"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-12-29
if i enter 'firefox', firefox opens. how would i fill in *blank* in 'blank firefox' in order to close it? i already know about 'xkill' and just plain ol' clicking the X on the window.

---

### Post by az on 2005-12-29
killall firefox
or 
kill -9 PID

---

### Post by ed_d on 2005-12-29
First: ps -ef | grep "name of program"

second, to really "kill it": kill -9 "name of program"

Main one I use, does the trick for me.

---

### Post by fuscia on 2005-12-29
oh, well here's a problem: 'killall' seems to work with everything but firefox and mozilla-thunderbird. i used the instructions here [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to install firefox 1.5 over 1.0.7, and used these instructions to try and install thunderbird 1.5 over 1.0.7(?) [http://doc.gwos.org/index.php/ThunderbirdNewVersion](http://doc.gwos.org/index.php/ThunderbirdNewVersion) but it never worked. i'm guessing the problem with the 'killall' command and these two programs is linked to how i upgraded them, maybe?

---

### Post by cwaldbieser on 2005-12-29
[QUOTE=fuscia]oh, well here's a problem: 'killall' seems to work with everything but firefox and mozilla-thunderbird. i used the instructions here [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to install firefox 1.5 over 1.0.7, and used these instructions to try and install thunderbird 1.5 over 1.0.7(?) [http://doc.gwos.org/index.php/ThunderbirdNewVersion](http://doc.gwos.org/index.php/ThunderbirdNewVersion) but it never worked. i'm guessing the problem with the 'killall' command and these two programs is linked to how i upgraded them, maybe?[/QUOTE]
The problem you are probably running into is that when you run "firefox", it is just a script that runs "firefox-bin" and then exits.  You need to kill firefox-bin.

Also, while "kill -9 PID" is a good way to shut down a hung process, it pays to try "kill -HUP PID" first, as this will allow a program to shut down normally if it is able.

---

### Post by amohanty on 2005-12-29
[QUOTE=fuscia]oh, well here's a problem: 'killall' seems to work with everything but firefox and mozilla-thunderbird. i used the instructions here [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) to install firefox 1.5 over 1.0.7, and used these instructions to try and install thunderbird 1.5 over 1.0.7(?) [http://doc.gwos.org/index.php/ThunderbirdNewVersion](http://doc.gwos.org/index.php/ThunderbirdNewVersion) but it never worked. i'm guessing the problem with the 'killall' command and these two programs is linked to how i upgraded them, maybe?[/QUOTE]


No. it should not matter. [killall ]("http://www.manlib.com/man/147") works at the process level and doesnt really care about who, what, where or how as long as it can locate the process. It is however possible that ff or thunderbird is not responding properly to a SIGTERM, unlikely but possible.

So what exactly happens when you issue a killall firefox?
Also I think if you look it up by process name: ps aux | grep fox the process name might be mozilla-firefox and not just firefox (cant confirm right now - nto on my box)

AM

---

### Post by fuscia on 2005-12-29
[QUOTE=cwaldbieser]The problem you are probably running into is that when you run "firefox", it is just a script that runs "firefox-bin" and then exits.  You need to kill firefox-bin.[/QUOTE]

aha! cried the witch, that was it! thanks, everybody.

---

