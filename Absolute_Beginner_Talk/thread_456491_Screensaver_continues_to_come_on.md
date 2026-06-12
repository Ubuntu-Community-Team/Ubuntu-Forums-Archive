---
title: "Screensaver continues to come on"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by virgilnilson on 2007-05-27
Every 10 minutes of inactivity my screen goes black (default screensaver). I've gone to system -> preferences -> screensaver and unchecked the box that says to kick in when the computer has gone idle. I've even set the slider to 2 hours, neither of those seem to have worked.

Is there something I may be missing?

---

### Post by oilchangeguy on 2007-05-27
try, system, pref, power mgt. adjust the slider that controls when the monitor shuts off.

---

### Post by kyphi on 2007-05-27
> unchecked the box that says to kick in when the computer has gone idle

Better put that checkmark back in.

---

### Post by virgilnilson on 2007-05-27
> **oilchangeguy said:**
> try, system, pref, power mgt. adjust the slider that controls when the monitor shuts off.

I have set that to never. The default was 40 minutes, but this was happening after only 10 minutes of inactivity.

---

### Post by virgilnilson on 2007-05-27
> **kyphi said:**
> Better put that checkmark back in.

Why is that? It says "Activate screensaver when computer is idle". I do not want to have a screensaver, so I would not want it to ever activate, so I would assume it should be unchecked.

---

### Post by kyphi on 2007-05-27
> Every 10 minutes of inactivity my screen goes black (default screensaver)

Perhaps I misread the above.

---

### Post by virgilnilson on 2007-05-28
This problem remains unsolved, it is rather annoying as I have to move the mouse every 10 minutes while I watch movies.

Anyone have an idea?

EDIT: Just so you guys can see that I'm not crazy, this is what the settings are at. The screen continues to go black every 10 minutes.

[IMG]http://img147.imageshack.us/img147/569/screenshot1du1.png[/IMG]

---

### Post by BaffledMollusc on 2007-05-28
I have exactly the same issue, and it's driving me nuts. No matter what power management / screensaver settings I choose, I get a blank screen after a few minutes.

Any suggestions would be helpful...

---

### Post by ramjet_1953 on 2007-05-28
I hope that I'm not stating the obvious here, but have you checked your BIOS settings?

Some BIOS's have a screensave feature.

In most cases, a BIOS setting overrides a software setting.

It may be the issue here.

Regards,
Roger 8)

---

### Post by Ek0nomik on 2007-05-28
I would first check what ramjet suggested.

I know this isn't an exact solution, but perhaps you can get some insight into the problem here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969)

---

### Post by virgilnilson on 2007-05-28
> **Ek0nomik said:**
> I would first check what ramjet suggested.

I know this isn't an exact solution, but perhaps you can get some insight into the problem here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/46575)
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/30969)

I've attempted all of those solutions including the xorg.conf edits and the terminal commands, none of them have worked.

I have also scoured my bios and there is nothing to do with a monitor power save.

---

