---
title: "MythTV Missing Guide Data"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by dlb on 2006-12-02
Hi all,

I'd like to thank everyone who posts on these forums, especially those who have contributed to the MythTV discussions.  Without your help, I'd still be staring at a pile of hardware, scratching my head trying to figure out how get it to work.  With Hyam's (great!) guide, as well as the help of others on here, I've been able to put together a MythTV 0.20 system on Dapper Drake.  There are still a few minor glitches to work out, but other than that it's fully functional and working great.  

A few of the bigger problems I'm having are this:

1)  MythTV will occasionally lose program guide data.  Usually it occurs after midnight and lasts for 1-2 days.  For example, I could have guide data for a Tuesday, but if I look to Wednesday's data, it will show "NO DATA" in the MythWeb guide.  I forget what it says on the front end ("Unknown", I believe), but you get the idea.  Looking past Wednesday, the data will usually go back to normal sometime on Thursday or Friday.  

Has anyone experienced this?  I have the normal 2 weeks of guide data except for these random missing 1-2 days.  I haven't been able to determine a common factor as to when this occurs, and when I notice the problem I'll usually ssh in and run the mythfilldatabase program manually.  I tried to remedy this by making a cron job to run mythfilldatabase automatically 4 times a day (every 6 hours), thinking that in the event that the data got corrupted it would be corrected 6 hours later by another run of mythfilldatabase.  However, even with this the problem is still occurring.

2)  The second of these issues is that it will randomly lose audio after a restart.  The remote volume controls don't display anything on the screen when this happens, which seems to indicate that it might be a problem with audio drivers not being loaded at all?  It happens randomly, but sometimes when I need to power down and then restart it will lose audio.  It generally takes 2-3 restarts before it comes back.  Luckily the machine is very stable and we only rarely lose power.

I seem to remember reading about registers not being cleared out; I believe the solution was to unplug the machine to allow them to discharge and then plug the machine back in.  I'm not sure if this would work in this situation.

Thank you in advance for your replies.  I hope I've given enough information, but if not, please let me know.

---

### Post by jlr4u on 2007-01-08
DId you ever get your issue with missing data resolved?  I am having the identical problem with my  channel guide missing data, but if I go forward a day I see if change from unknown to good data.

---

### Post by dlb on 2007-01-09
Hi there,

I haven't noticed it in a while, but that could just be coincidence since I haven't been watching as much TV lately.  I found that setting up a cron job to run mythfilldatabase every 6-8 hours will sort of fix it, since any missing guide data is usually corrected the next time it runs.

Sorry I couldn't be more help, good luck!

---

