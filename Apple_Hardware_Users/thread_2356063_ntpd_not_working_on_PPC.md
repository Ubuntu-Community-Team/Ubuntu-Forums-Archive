---
title: "ntpd not working on PPC"
date: 2017-03-19
forum: Apple Hardware Users
---

### Post by katakaio on 2017-03-19
Hello folks,

I just inherited a Mac mini G4 (circa 2005) and I'm in the process of turning it into a home server. Everything is working surprisingly well so far, but one thing that has not worked is getting ntpd running. I use ntpd to serve time to my home network and also for some applications on the server that require precise time.

However, it seems that ntpd is unable to update the local time on this PPC machine, incurring abnormally large offset and jitter values for every upstream server within minutes of starting. I can perform an initial synchronization with ntpdate without issue, but ntpd seems unable to keep the clock in sync. When exploring with the ntptime command, I get error code 5 (TIME_ERROR) as described [here]("http://lkml.iu.edu/hypermail/linux/kernel/0503.1/1296.html") and [here]("https://groups.google.com/forum/#!topic/comp.protocols.time.ntp/_HJ8a5DPU5Y"). I've never experienced this issue on Intel/AMD boards.

Has anyone successfully configured ntpd on a PPC installation? If so, please tell me what magic you used! Thanks.

---

### Post by ernsteiswuerfel on 2017-03-19
Ubuntu is systemd-based for a long time, so why not simply use **timedatectl set-ntp yes**. ;-) You can check the settings with **timedatectl status**. Or do you have a specific need for ntpd?

---

### Post by SeijiSensei on 2017-03-19
First, I'd try setting the hardware clock with the hwclock utility.  Use ntpdate to get the current time, then run
```
sudo hwclock --systohc
```
which will set the hardware clock to the system time.

If that doesn't help, maybe you need a new battery for the clock.

---

### Post by katakaio on 2017-03-20
> **ernsteiswuerfel said:**
> Ubuntu is systemd-based for a long time, so why not simply use **timedatectl set-ntp yes**. ;-) You can check the settings with **timedatectl status**. Or do you have a specific need for ntpd?

I *do *have a specific need for ntpd, as stated in my post: serving time to my home network and keeping very precise time.

> **SeijiSensei said:**
> First, I'd try setting the hardware clock with the hwclock utility. Use ntpdate to get the current time, then run
```
sudo hwclock --systohc
```
which will set the hardware clock to the system time.

If that doesn't help, maybe you need a new battery for the clock.

Good tip about resetting the hardware clock...since this unit hasn't been powered on in years, that was definitely way off! So far, ntpq -p is reporting slightly more reasonable values for offset and jitter, but they're still climbing, albeit more slowly. I'll let it slew overnight and report back what I find. Thank you!

---

### Post by katakaio on 2017-03-21
Alas, the hwclock suggestion didn't do it...after ~10 hours, I still have offset and jitter values anywhere between 600 and 800 ms for each server. I've ruled out any network interference, as an Intel-based machine on the same network has no issues (i.e. offsets < 10 ms and jitter < 5 ms for nearly every server). Next stop is the battery!

---

