---
title: "gsynaptics not working"
date: 2008-04-19
forum: Absolute Beginner Talk
---

### Post by Doormat on 2008-04-19
I believe I setup my xorg.conf correctly for gsynaptics but I still get the error from gsynaptics (set SHMCONFIG etc.) attached is my xorg.conf. I run 8.04 beta and I have rebooted since editing xorg.conf

---

### Post by quirks on 2008-04-19
The GSynaptics homepage ([http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)) says:
> To use your setting values at each starting of Xserver, you have to run gsynaptics-init at the starting of Xserver.

Have you run that command after you logged in?

EDIT: Nevermind, I just realized you probably did, otherwise, you wouldn't have received the error. However, I found a bug report, that might not please you: [https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/155119](https://bugs.launchpad.net/ubuntu/+source/gsynaptics/+bug/155119)

---

### Post by anewguy on 2008-04-19
I ran gsynaptics on my old laptop without a problem, and I believe the init is done automatically once you've installed, as I never had to run that.  Keep in mind this was with Feisty and Gutsy - not Hardy.  The bug report mentioned by quirks is interesting - maybe certain types of laptops run into this - I never did.  Also have you tried changing "true" to "True"?  It's been quite a while now since I used that laptop, but for some reason I'm thinking it was a capital "T" - then again, it may not be case sensitive at all !! ??  :)

---

### Post by quirks on 2008-04-19
Yeah, you might also want to try setting the parameter to "1" or "on". I found several posts on the Internet, where people used these values. However, I am sceptical as to whether this works.

---

