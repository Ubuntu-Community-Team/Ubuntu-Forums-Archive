---
title: "Identifying cause of spontaneous reboots"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by 5circles on 2008-02-15
Does anyone have recommendations to figure out why I'm getting spontaneous reboots?

I've only just realized this was happening with one of the computers since it doesn't do much other than run WM Timetracker and a WordPress blog for the house.  It restarted this afternoon while I was watching so I started investigating.  According to what I see in /var/log/messages, it has been rebooting every morning at roughly the same time (within a minute or two), when it should be totally idle.  And then there are occasional reboots at other times.

It seems doubtful that there is a temperature issue because there isn't anything happening and this machine has been stable for a while.  But I'm looking into ways to check the temperature. There is no ACPI support.

The machine is an old (very old I guess) Dell XPS 500,  500 MHz processor, 512Megs RAM, plenty of disk space. It seems to be using about 11% of CPU and 27% of memory when idle.  I'm running 7.04.

Thanks
Mike

---

### Post by dcstar on 2008-02-15
> **5circles said:**
> Does anyone have recommendations to figure out why I'm getting spontaneous reboots?

I've only just realized this was happening with one of the computers since it doesn't do much other than run WM Timetracker and a WordPress blog for the house.  It restarted this afternoon while I was watching so I started investigating.  According to what I see in /var/log/messages, it has been rebooting every morning at roughly the same time (within a minute or two), when it should be totally idle.  And then there are occasional reboots at other times.
.......

The first thing I would do is try and determine if there are any possible things in your home (or close by) that could cause power spikes at the times you have these issues.

People with water heaters on timers (or other similar high current devices) have been known to have these things crash PCs - sometimes a good power board with surge filtering can make all the difference.

---

### Post by ace007 on 2008-02-15
Originally I thought your problem sounded like a hardware issue.  I have had this problem two tiimes on the same desktop in the past.  Both times it was running Windows, but thats irrelevant.  The first time it was because the power supply was on its way out to pasture.  It happens often and you may want to investigate it before running to the store to buy a new one.  The other time it happened to me it wasn't the power supply, it was an overheating issue.  

So, I thought that was your problem, but since you point out it happens so periodically, it may be a different problem.  My suggestion: your first step should be to decide if it's the power suypply. So try testing the computer on another power supply.

---

### Post by 5circles on 2008-02-15
I think the most likely thing is a surge from a neighbor.  I've checked my timers and there isn't anything around that time.  The circuit the system was on seems a little flaky, so I have moved it to a different breaker.

It could be that the power supply is either on its way out, or just more susceptible than my other systems.  But it is probably not worth changing it out because the Dell power supplies aren't compatible, and this machine is already past its use by date.  A new machine might be a better option.

I will keep an eye on the /var/logs/messages file and see if moving to the other circuit helps.

Thanks
Mike

---

### Post by oilchangeguy on 2008-02-15
> **5circles said:**
> I think the most likely thing is a surge from a neighbor.  I've checked my timers and there isn't anything around that time.  The circuit the system was on seems a little flaky, so I have moved it to a different breaker.

It could be that the power supply is either on its way out, or just more susceptible than my other systems.  But it is probably not worth changing it out[COLOR="Yellow"] because the Dell power supplies aren't compatible[/COLOR], and this machine is already past its use by date.  A new machine might be a better option.

I will keep an eye on the /var/logs/messages file and see if moving to the other circuit helps.

Thanks
Mike

last i heard a power supply is a power supply. and as long as it will fit in the case, and is at least the same wattage, and has the same connectors. it will power the computer. it sure won't hurt to try.

---

### Post by 5circles on 2008-02-15
> **oilchangeguy said:**
> last i heard a power supply is a power supply. and as long as it will fit in the case, and is at least the same wattage, and has the same connectors. it will power the computer. it sure won't hurt to try.

Unfortunately Dell (at least old boxes) power supplies aren't compatible.  I changed on a few years back and discovered this.  I think the connections aren't exactly the same, for some reason.  It is a bit of a shame because I would like to use this box for some low level tasks, but not if it isn't reliable.

---

### Post by 5circles on 2008-02-16
This is odd, or maybe I am misinterpreting the entries in /var/log/messages.

I left the machine logged in last night.  When I checked this morning it was as I left it, so it looked like there hadn't been a reboot.  But there is still an entry in the /var/log/messages:
```
Feb 16 07:37:03 linuxbox syslogd 1.4.1/20ubuntu4: restart.
```
Is this entry just something running daily?  I see now that the restarts I manually started from the console have a signal 15 entry first and then the next entry is 'inspecting /boot/System.map'.  The spontaneous restarts and the restart from me pushing the reset button don't have the 'signal 15' line, but still have the line for inspecting.

So it looks like the problem isn't the scale that I thought.  The log shows that it happened 6 times this month at random days and times.  It still looks like a power problem though.

Can someone explain the 7:35 am entry in the messages file?

Thanks
Mike

---

