---
title: "Battery not recognized"
date: 2010-04-24
forum: Apple Hardware Users
---

### Post by zeroti on 2010-04-24
I'm using lucid on a ppc powerbook and had the same issue with karmic. Power Management doesn't know that my laptop uses a battery. The battery icon doesn't show up above if I check "only display an icon if battery is present," and when I check "always display an icon," a plug is always shown, never a battery.

Is there a way to get ubuntu to recognize my battery?

---

### Post by ditsch on 2010-04-24
```
sudo modprobe pmu_battery
``` worked for me. I added it to /etc/modules so it gets loaded on boot automatically.

---

### Post by zeroti on 2010-04-24
> **ditsch said:**
> ```
sudo modprobe pmu_battery
``` worked for me. I added it to /etc/modules so it gets loaded on boot automatically.

thanks, that worked like a charm! :)

---

### Post by zeroti on 2010-04-24
Ok, one small issue: the battery icon is shown when I have my laptop plugged in. clicking it says that the battery is discharging, and the computer goes to sleep early because it's using the battery power-saving settings and not the ac power settings. otherwise, it seems ok.

---

### Post by tgalati4 on 2010-04-24
I think that is normal, but annoying behavior.  The apple charging circuit on PPC charges the battery to 100% then lets it drain to 95% then starts the charging again.  You can change this behavior, but you will have to research how to do that.  My guess is that there are option switches for pmu_battery.

---

### Post by paulinchen on 2010-04-29
Is there a comparable command for intel-mac users as well? Cause I'm having the same problem that the battery isn't recognized. Only when I was in OSX and make a reboot to Lucid I can get the battery in the panel.

---

### Post by Matt Brooks on 2010-06-21
when i input the command 

sudo modprobe pmu_battery

all i get is

matt@matt-laptop:~$ sudo modprobe pmu_battery
FATAL: Module pmu_battery not found.
matt@matt-laptop:~$

---

### Post by Matt Brooks on 2010-06-21
Here is a screenshot of my battery stats

---

### Post by ditsch on 2010-06-22
Sorry, I doubt this is an iBook or a Powerbook.

---

### Post by alexmurray on 2010-06-22
> **paulinchen said:**
> Is there a comparable command for intel-mac users as well? Cause I'm having the same problem that the battery isn't recognized. Only when I was in OSX and make a reboot to Lucid I can get the battery in the panel.
You're probably being hit by this bug: [https://bugs.launchpad.net/libusb/+bug/427805](https://bugs.launchpad.net/libusb/+bug/427805) - see the last comment for how to enable the proposed updates repo to install and test the fix - if it works for you with this update, please comment as such on the bug report.

---

