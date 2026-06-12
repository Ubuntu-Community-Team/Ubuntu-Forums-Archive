---
title: "on and off"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by abu-fatu on 2006-10-13
is there an option where i can schedule dapper to shut and turn itself off and on?

---

### Post by kidders on 2006-10-13
Hi there,

Pretty obviously, there's no way Ubuntu can turn your machine *on* for you, but you _can_ make it turn it *off*.

You can use commands like **poweroff** to power off your machine. Additionally, you could try **shutdown -h  18:30** or **shutdown -h  +60**, to kill your machine at half six, or after 60 mins, respectively. On top of that, you could always schedule a shutdown with cron, in the event you wanted your computer to shut down at the same time every Tuesday, perhaps.

Turning your box back on again is the responsibility of your BIOS, assuming it supports the feature.

I hope that helps.

---

