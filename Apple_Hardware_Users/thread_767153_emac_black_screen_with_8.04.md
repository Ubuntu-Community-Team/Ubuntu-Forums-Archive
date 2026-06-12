---
title: "emac black screen with 8.04"
date: 2008-04-25
forum: Apple Hardware Users
---

### Post by michaelpagz on 2008-04-25
Hello, I am trying to install 8.04 on an eMac. I get a black screen soon after boot.I've gotten to terminal after booting. This computer has never run linux before. I'm installing from scratch.  Is there any fix to this black screen?  Is it just not going to work? I saw some other posts involving yaboot.conf but it didn't seem to work for me. I may not have executed it properly or my issue may be unique because its 8.04. 
 Thank you very much,
Michael

ps. I realize the board is probably going nuts with the new release coming out. Sorry to add to the chatter.

---

### Post by stream303 on 2008-04-26
Welcome aboard!

Looks like we may still have to manually edit our xorg.conf files.  I believe the biggest sticking point for emacs was the vertical and horizontal frequencies needed to be manually specified, as well as possibly turning dri off, and even experimenting with FBDev.  Maybe.

Check out this thread in from the ppc archives that might help:

[http://ubuntuforums.org/showthread.php?t=695325](http://ubuntuforums.org/showthread.php?t=695325)

We're all kind of pioneers right now with hardy, so hang in there!

---

