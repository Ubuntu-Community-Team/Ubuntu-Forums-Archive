---
title: "Schedule - see if/why a scheduled command failed"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by dacium on 2008-01-22
I put two enteries in system tools -> schedule, and they appear when i do command crontab -l
They worked for a couple weeks (running once per week), but for some reason one of the commands no longer seems to get executed. If i run the command manually, it appears to work fine.

Is there a log anywhere that I can see if the system actually ran the command?
If the system is shut down at the time it is meant to run, does it run it at next boot up?

The jobs are both recurrant with settings:
0 10 * * 1
0 12 * * 1
However the second one appears to have stopped working for no reason.

---

### Post by dacium on 2008-01-22
bah never mind I think the second command depends on the output of the first command, but it was still processing and seems to take more than 2 hours now.

---

