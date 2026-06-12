---
title: "session mamager blues"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-11-09
My session manager is messed up (menu-->system-->preferences-->sessions).
I cannot save any programs on the "Startup programs" tab. (I define them but when I reopen the manager they are gone).
Is there an alternative way (perhaps through terminal) to set startup programs?
Is there a fix for the session manager?
I know others have this problem as well in the forum but it remains unanswered....

---

### Post by MasterOfDisaster on 2006-11-09
From the Novell website:

[http://www.novell.com/coolsolutions/tip/8959.html](http://www.novell.com/coolsolutions/tip/8959.html)

Not sure if the same in Ubuntu, as I am on my families computer (Windows).  Anyways, I've noticed the problem as well, although only for compiz-tray-icon.

---

### Post by geokok1981 on 2006-11-10
Thanks but the solution seems to be non valid for ubuntu since the 
suggested path does not exist (at least in my pc :) ).
This should be rather easy to fix right?
However I cant find a relevant bug in launchpad so I guess it wont be
fixed soon by the devs....

---

### Post by rlozano on 2006-11-10
> **geokok1981 said:**
> My session manager is messed up (menu-->system-->preferences-->sessions).
I cannot save any programs on the "Startup programs" tab. (I define them but when I reopen the manager they are gone).
Is there an alternative way (perhaps through terminal) to set startup programs?
Is there a fix for the session manager?
I know others have this problem as well in the forum but it remains unanswered....

you using edgy? i seem not to have the problem. let me double check the startup config file.

---

### Post by geokok1981 on 2006-11-10
It seems that the problem appears to some users while not on others.
I found a workaround in the forums [http://ubuntuforums.org/showthread.php?t=286883](http://ubuntuforums.org/showthread.php?t=286883) (proof that others face the problem too).

Also I filled a bug report at launchpad here:
[https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200](https://launchpad.net/distros/ubuntu/+source/upstart/+bug/71200)

please go there and confirm the problem if u face it too....

ps. yes I am on edgy

---

