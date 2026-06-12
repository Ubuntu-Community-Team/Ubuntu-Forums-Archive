---
title: "NTP problem"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by phredduk on 2007-04-22
Hi all,

I'm having major problems keeping my time correct! This should be a simple task, no idea what's going on:

I can set my time via 'time-admin' and clicking "synchronise now", that works fine. After a couple of hours, the time creeps out of sync by about 10 minutes or so.

If i choose the 'keep clock synchronised with internet servers' the problem gets worse, and the time ends up out by an hour! It doesn't make sense to me because i can manually sync the time with no problems.

Anyone have any suggestions as to what's going on here? :confused: 

Many thanks

---

### Post by mikeyphi on 2007-04-22
It's possible that your on-board BIOS battery is on the way out! It's easily replaceable on newer computers but might be hardwired on older systems.

---

### Post by phredduk on 2007-04-22
Thanks, i'll check my BIOS time next time i reboot, might need a new CMOS battery, this mobo is 3 years old, and rarely switched off..

I still don't understand why the time drifts out when I choose 'Keep clock syncronised with Internet servers', surely this should take the time from NTP and ignore my BIOS clock?

---

### Post by canadianwriterman on 2007-04-22
I'm having the same problem on my final Feisty install on a year-old HP desktop. Sometimes the NTP synch setting actually changes on its own to "manual." Also the NTP setting under "Processes" sometimes unchecks itself. When I power off the computer is the worst. If I power back on in the morning, the time is way off... by hours. Didn't have this problem with the beta.

---

### Post by phredduk on 2007-04-23
canadianwriterman - sounds like a similar problem to mine apart from: I'm running Edgy (last time I did a dist-upgrade things went pretty pair-shaped, so I'm gonna do a fresh install on my next machine)

Also the auto-sync option seems to stay checked, just doesn't seem to work - 'synchronise now' works, but the 'stay synced' option does not - weird.

---

### Post by canadianwriterman on 2007-04-24
phredduk,

I MAY have solved my issue. I think the problem started when I installed Feisty and chose UTC during the install. I reinstalled Feisty completely and this time I chose NOT to use UTC. When booted up, I installed the NTP support, synchonized manually, then set for Internet synch. This morning, I rebooted and it seemed to be fine. The PC is shut down all day today. When I get home, I'll boot and see if the correct time sticks.

---

