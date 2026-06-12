---
title: "Wake On LAN Utility Needed For XP/W7"
date: 2012-03-14
forum: Any Other OS
---

### Post by Roasted on 2012-03-14
I'm on the hunt for a WOL utility for XP and W7 that can send a WOL packet at a specific time. My plan is to have all systems on the LAN send a WOL packet to kick on my backup server at 5:55 PM, then at 6:00 PM, all data rsync's over (syncback free for the Windows boxes) to the backup server. Then, an hour after inactivity, the backup server goes back to suspend mode. That way the box isn't running 247 when it's only needed for a little bit a day.

Is there such a thing for XP and W7? I've already got the Linux clients taken care of (it was pretty stinkin easy... just install wakeonlan and crontab "wakeonlan 11:22:33:44:55:66". Total win), but like I said, just drawing a little bit of a blank on the Windows systems...

---

### Post by mips on 2012-03-14
Just so I understand you correctly you want the clients (PCs) waking up your backup server?

I'm assuming your clients stay powered on 24/7 and you don't need to wake them up?

Why don't you just let the linux clients wake up the backup server at the specified time? Why does every client have to send a wakeup packet?

Edit: Have a look at this [http://forums.techguy.org/dos-other/778427-help-needed-schedule-task-thru.html](http://forums.techguy.org/dos-other/778427-help-needed-schedule-task-thru.html)

---

### Post by Roasted on 2012-03-14
> **mips said:**
> Just so I understand you correctly you want the clients (PCs) waking up your backup server?

I'm assuming your clients stay powered on 24/7 and you don't need to wake them up?

Why don't you just let the linux clients wake up the backup server at the specified time? Why does every client have to send a wakeup packet?

Edit: Have a look at this [http://forums.techguy.org/dos-other/778427-help-needed-schedule-task-thru.html](http://forums.techguy.org/dos-other/778427-help-needed-schedule-task-thru.html)

Currently my mom's laptop (W7) only has Windows on it... she'll be getting dual booted in a few days, though. My brothers dual boot because they're gamers, but they still spend some time in Linux. It comes in waves though. At times they'll be in Linux nonstop, other times they won't touch it for weeks. That's why the Windows systems initiating the WOL is equally as important.

I'm going this direction with waking up the backup server so that way it's convenient to the clients. I don't want systems firing up on their own and the family being all, what the? I'd rather just the systems quietly call for the backup server when they need, that way its as transparent as remotely possible to the end user.

Thanks for the info, by the way!

---

### Post by mips on 2012-03-14
Ok, I see now.

Let us know if that info was useful ;)

---

