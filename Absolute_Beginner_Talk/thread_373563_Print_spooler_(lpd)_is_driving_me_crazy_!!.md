---
title: "Print spooler (lpd) is driving me crazy !!"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-03-01
Just finished setting up cups last week on my home network and all went very well. I can print from any of my three comps (one Dapper only, laptop dual boot Dapper and XP, and one XP only). Problem is in the past four days I keep getting lpd daemons starting up using 100% cpu and over half of my cache space in memory on the laptop (Toshiba Satellite Pro - 768 RAM -40 Gig hd - Pent D processor). I ran "top" in terminal and when the comp cpu goes to 100% and stays there for more than 10 or 15 seconds it is due to an lpd daemon running. As far as I can tell this has something to do with the print spooler. If I run "sudo kill <daemon ID> in terminal it kills the daemon, but five minutes later another one with a different ID starts up again. Any Idea how to stop the lpd daemons from starting up. I don't have anything queued up on the printer and no print jobs pending, and put the printer on pause with no effect. Any help would be appreciated, this is very annoying.

---

### Post by jerrynewt on 2007-03-01
Any ideas out there ??

---

