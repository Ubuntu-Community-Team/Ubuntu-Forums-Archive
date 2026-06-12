---
title: "Automatic Updater does not appear in System Trary"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by lazyrussian on 2007-03-27
I'm using Kubuntu and for some reason the icon that used to pop up in my system tray and inform me that there were new updates for me in adept has disappeared...the only way I know that there is an update is if I open up adept and check.

Anyone know how to fix this?

---

### Post by lazyrussian on 2007-03-27
*bump*

---

### Post by mahiyar on 2007-03-27
I do not know about kubuntu but in Ubuntu I had inadvertently removed system update icon (it just a thin line) from the bar, I later restored it by right clicking the bar and adding system update applet.

---

### Post by lazyrussian on 2007-03-27
I don't seem to have that option - I mean I do have applets I can choose from, but nothing that allows me to see when there are new system updates.

---

### Post by lazyrussian on 2007-03-27
I  think I might just fixed it.

For those who run into this problem, go to adept updates and install/reinstall the following package: **adept-notifier**

Hopefully I'll see something come up in the next few days when there is a new update out.

---

### Post by lazyrussian on 2007-03-29
ok I guess I was wrong. There was an update todayf or an open office but the update icon didn't appear in the system tray. I only found out because I opened adept and saw the update.

I guess I'm still stuck with this problem :(

---

### Post by lazyrussian on 2007-03-29
*bump*

---

### Post by ahabahab on 2007-04-02
Maybe reinstalling the update-notifier package would do the trick?

---

### Post by lazyrussian on 2007-04-02
Thanks for the advice. I reinstalled It - I'll see what happens in the next week or two and I'll post back an answer.

---

### Post by lazyrussian on 2007-04-04
Alright, their were updates today and it didn't work :(
Again, the only way i found out was due to the fact that I opened adept for various different reasons.

---

### Post by serfcx on 2007-04-04
Having same problem with recent install of Ubuntu 6.10. I had installed Ubuntu 6.10 on another PC about a month ago and the notifyer works fine, the recent install doesn't - no apparent difference between systems.:confused:

---

### Post by umphlette on 2007-07-28
I'm seeing this problem in Gnome with a Fiesty install.  I've been up and running for some time and have never seemed to get notified of updates like I did under Edgy (and dapper and breezy too...), so I resort to manually checking for updates via Synaptic or by apt-get update.  As a side note, I normally run the desktop as root for personal reasons...I don't know if that is somehow contributing to the problem...

I don't quite know what the update notifier does to check for updates but if it's using Cron maybe that part was broken somehow?  Anyone else know what's up or have any ideas?

---

