---
title: "Displaying Battery Charge in Indicator Area"
date: 2010-10-15
forum: Apple Hardware Users
---

### Post by zeroti on 2010-10-15
I'm on a Powerbook with 10.10 installed. The battery icon doesn't show up in the indicator area next to the sound volume when I'm unplugged unless I select to have the icon displayed even when my computer is plugged in. And even then, it doesn't show current battery charge.

I have added pmu_battery to /etc/modules , and /proc/pmu/battery_0 has relevant information on battery charge, and emacs seems smart enough to know my battery level.

I tried to install pmud, and but that conflicts with pbbuttonsd and removing that would remove ubuntu-desktop! :O (I would like to try pmud and pommed, as those seem to have a better feature set than pbbuttonsd.)

Any ideas on how to install those or get the battery display to work? Thanks.

---

### Post by bd1308 on 2010-10-17
You're not alone. Same thing here. I'm on a 1.33Ghz Powerbook G4 (that i really want to overclock)

/proc/pmu/battery_0 reports the time left in what units? I'm guessing seconds.

None of the updates I have gotten seemed to fix the problem.

I'm going to try 10.04 since it's a LTS version....

I'm just thrilled most everything else works (except for brightness)

My cpu usage is very low even when running at 667Mhz.

B

---

### Post by zeroti on 2010-10-18
> **bd1308 said:**
> I'm just thrilled most everything else works (except for brightness)


Brightness works for me. Try modprobe-ing i2c-dev and/or pmu_battery.

If that fixes it, then add them to /etc/modules .

---

### Post by madlock on 2010-10-21
Same Problem on iBook G3 with 10.10!

---

