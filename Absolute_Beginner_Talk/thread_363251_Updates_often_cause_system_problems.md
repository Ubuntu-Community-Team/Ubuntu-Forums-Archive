---
title: "Updates often cause system problems?"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by eridon on 2007-02-16
Hello all,

I'm very new to Linux with about 4 weeks of experience.  Currently running Ubuntu 6.10 which has been running great.  For about the last 2 weeks I've been running Beryl which I found as a nice eye candy item.  So today I run the recent Ubuntu updates (been away for a few days) and it asked me to restart (pretty rare).  As soon as I restarted I ran into a problem where the system wouldn't load the X server and I was stuck at the command line.

After a quick search of the forums I found a recomendation to run dpkg-reconfigure xserver-xorg after starting up in restore mode.  After answering the 104 questions my system was able to boot up the X server but with no Beryl.  and the real killer is I get another 22 updates, feeling real confident about installing these.  Now I suspect my current issue is a driver problem but that's not my questions atm.

How often do things of this nature happen?  One of the reasons I decided to try Linux was due to the famed stability.  In just a month of use this is the 2nd time my system got hosed after running the updates.  I'm hoping this is something maybe I'm doing wrong.  I've been surprised by the sheer number of daily updates and the idea having having to fix it every 2 weeks does not appeal to me.  So in general how reliable are these updates?

---

### Post by nhandler on 2007-02-16
For the most part, they are pretty stable. Are you running dapper, edgy, or feisty? Feisty still is in the pre release state, so it still has bugs. If you are running dapper or edgy, it should be stable.

---

### Post by eridon on 2007-02-16
I believe Ubuntu 6.10 is Edgy.  As I'm just starting out I figured it would be best to stay away from Feisty.

---

### Post by Cariboo1938 on 2007-02-16
OK, maybe it's stable...but the point is, and I think that's what [COLOR="Purple"]eridon[/COLOR] is talking about, ...specially kernel updates seem to be a problem. I had the same issue twice that the X server didn't load. And I'm still stuck with the latest kernel update to 2.6.17-11 generic, after reboot I end up with the black screen!

**Now I got it working ---see attached file!**

---

### Post by old_geekster on 2007-02-16
The only time that you have to reboot is after a major system update.

I have run "Compiz" and "Beryl".  I found both of them to be much to unstable for my tastes.  I did a new complete install and have refrained from using them.

I have read some glowing reports, but like I said, I wasn't impressed.

---

