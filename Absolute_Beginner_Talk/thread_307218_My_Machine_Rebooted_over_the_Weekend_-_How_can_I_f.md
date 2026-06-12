---
title: "My Machine Rebooted over the Weekend - How can I find out the reason?"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by lowracer on 2006-11-26
I went out of town to visit relatives over the U.S. turkey day holiday.  I left "Einstein@Home" and Azureus and some other random stuff running.  Both cores were at 100%.  Fans were all running and system temps looked good.  When I came back home a few days later, The machine was presenting me with the Ubuntu login screen.  When I logged in and checked the uptime, it showed just under 8 hours.  So sometime that day it had been rebooted.

No one has access to my house.  There was no sign of a break-in.  The jewelry and other goodies were not taken.  

Is there some way to tell why the system rebooted?  Is there a log file or something similar that would give me a clue?  My machine is set to reboot on power fail, and I guess if that's the case I'll have to ask my neighbors if the power went out.

Thanks...
-Mark

---

### Post by bulldog on 2006-11-26
The only thing I know is that if one of your running application where malfunctioning,you should see a sign of a crash report in your notification area.

You can take a look in /var/log if there's any sign of what's happened when you where away.

---

