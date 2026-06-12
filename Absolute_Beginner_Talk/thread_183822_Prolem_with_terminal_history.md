---
title: "Prolem with terminal history"
date: 2006-05-28
forum: Absolute Beginner Talk
---

### Post by wyohermit on 2006-05-28
My terminal history only lasts until I close the terminal window.  I have been running a seperate Dapper install, playing, experimenting and crashing it, using my Breezy install as my primary.  However I am now ready to switch over and use Dapper as my primary and make room for Edgy.  Anyway I digress.  I just noticed that my terminal history in Dapper would not go back any farther than the beginning of that particular window session.  I checked the profile settings and they seem to be in order. Is there someplace else I need to check to find out what I messed up.

---

### Post by wyohermit on 2006-05-29
Ok  Problem solved.
I had you guys looking for the wrong answer.  What I really should have said was that I had a problem with my bash history not terminal history.
It turns out that somehow my .bash_history file permissions had gotten set to root.  So a quick chown and chgrp and all is working fine now.

Ken

---

