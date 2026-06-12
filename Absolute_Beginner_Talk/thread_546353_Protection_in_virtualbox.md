---
title: "Protection in virtualbox"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by jpr13 on 2007-09-08
If I am running a Windows OS in Virtualbox, what do I have to do to protect it?

Do I set it up with a firewall/virus/spyware software just like I would with a standard windows installation, or is there another way to do it?

Is the VB OS safer than a native OS?

                                                    Jason

---

### Post by oilchangeguy on 2007-09-08
> **jpr13 said:**
> If I am running a Windows OS in Virtualbox, what do I have to do to protect it?

Do I set it up with a firewall/virus/spyware software just like I would with a standard windows installation, or is there another way to do it?

Is the VB OS safer than a native OS?

                                                    Jason

windows is still windows. makes no difference where it's located. so i'd protect it. why a windows vm? it will not have use of the computers full power (ram, cpu, etc.).

---

### Post by scxtt on 2007-09-08
if it's facing the outside world/network - it's as vulnerable as it would be on physical hardware ...

[quote=oilchangeguy]why a windows vm? it will not have use of the computers full power (ram, cpu, etc.).[/quote]by that logic, why use VMs @ all?  you should at least *attempt* to validate that statement, otherwise it just looks misinformed ...

---

### Post by b15h0p7 on 2007-09-08
> **oilchangeguy said:**
> windows is still windows. makes no difference where it's located. so i'd protect it. why a windows vm? it will not have use of the computers full power (ram, cpu, etc.).
QFE

---

### Post by jpr13 on 2007-09-08
I am just using VB so I can jump into windows fast to use certain programs, Microsoft Office and Veoh Player. I do most of my work in Ubuntu, but I just wanted Windows within easy reach.

                                                 Jason

---

### Post by oilchangeguy on 2007-09-08
> **scxtt said:**
> if it's facing the outside world/network - it's as vulnerable as it would be on physical hardware ...

by that logic, why use VMs @ all?  you should at least *attempt* to validate that statement, otherwise it just looks misinformed ...

uh, i did validate my statement. i said vm's don't have use of the computers full power. this is true. full power is needed for apps like games. perhaps, it is you who is misinformed.

---

### Post by scxtt on 2007-09-08
right, windows is ONLY for games - i forgot :rolleyes: ... we must use our +500 VMs here @ work for nothing useful @ all - this VM stuff is just a fad, cause really they're worthless since they "will not have use of the computers full power (ram, cpu, etc.)." ...

---

### Post by PilotJLR on 2007-09-08
Yeah, VI3 pretty much rocks.

It will be interesting to see when/if Xen reaches that level.

---

### Post by Malibu Illusion on 2007-09-08
The advantage of WMs is you can easily restore them to a previous state.  I wouldn't fret too much about protecting them when you can roll them back very easily at your leisure unless you're storing data you need to remain in tact on them for whatever reason, of course.

---

### Post by n3tfury on 2007-09-08
> **scxtt said:**
> right, windows is ONLY for games - i forgot :rolleyes: ... we must use our +500 VMs here @ work for nothing useful @ all - this VM stuff is just a fad, cause really they're worthless since they "will not have use of the computers full power (ram, cpu, etc.)." ...

indeed.  i'm using virtualbox for a couple of games, foobar, and some recording apps.  there's a need to VM XP for some folks.

---

### Post by scxtt on 2007-09-08
> **PilotJLR said:**
> Yeah, VI3 pretty much rocks.

It will be interesting to see when/if Xen reaches that level.we're still on VI2.0 here, running ESX3 for the most part ... can't wait til we can really (really!) have Vmotion working @ full potential :)

---

