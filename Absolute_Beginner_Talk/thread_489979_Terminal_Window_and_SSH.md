---
title: "Terminal Window and SSH"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by drhiii on 2007-07-01
Am trying to figure out... why when I go to a terminal window then ssh into another box... if I do not have any activity in that terminal window using ssh, it appears to timeout and just locks up.  If I ping something, or just press enter every couple of minutes, the windows stays active.   But it seems like if I leave it for more than 4 or 5 minutes, my ssh session just hoses and I have to relog on.   This happens going FROM an Ubuntu system to anything else, so I suspect it is a timeout of some type due to inactivity.  But for the life of me I cannot find a setting anywhere.

Thoughts anyone?  

tx

---

### Post by scxtt on 2007-07-01
lots of servers have no-activity timeout values ... most likely the server you're logging onto, not where you're coming from ...

for bash, it's TMOUT ... i did, **export $TMOUT=5** and after 5 seconds it logged me out automatically ...

---

### Post by drhiii on 2007-07-02
Ah, there's the rub... I have several Fedora servers and this does not happen when I go from Fedora to Fedora.  Or Windows SSH proggie to Fedora.  This happens when I go FROM an Ubuntu client or server to any flavor... Fedora, Ubuntu, so far these two.  I will look at the bash profile to see if this may be the culprit.  But it is not going to a server, but going from Ubuntu anything.  

Will dig down based on your ideas tho.  Thanks a mil for this...


> **scxtt said:**
> lots of servers have no-activity timeout values ... most likely the server you're logging onto, not where you're coming from ...

for bash, it's TMOUT ... i did, **export $TMOUT=5** and after 5 seconds it logged me out automatically ...

---

