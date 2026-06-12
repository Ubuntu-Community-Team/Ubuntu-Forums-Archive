---
title: "[SOLVED] How do I STOP Ubuntu from setting BIOS clock to UTC?"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by suomalainen on 2008-01-31
Ubunteros,

I have a tri- O/S system. All 3 O/S's are mounted in thier own individual racks. Only one rack can be on at any given time.

PROBLEM.
Ubuntu sets the BIOS clock to UTC and adjusts once OS loads. Windows XP reads wrong time and uses it. i.e. UTC

This means anytime I use XP or 2000 I must open bios first to set right time.

What is the fix for this? 

Thanks

---

### Post by 1337455 10534 on 2008-01-31
In windows, in the time widget on the bottom right (sorry for sounding like an idiot, i barely use windows now), set it so that it syncs with time.windows.com every 2 seconds. Well, more like every hour, but I think there is an option to sync at boot.

---

### Post by suomalainen on 2008-01-31
You misunderstood me. I want the BIOS clock to always show local time! Not UTC time.

---

### Post by lfmoreno on 2008-01-31
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=633848](http://ubuntuforums.org/showthread.php?t=633848) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The thread below fixed the issue for me.

Regards,

If turning off UTC does not work in the clock applet try to change it manually.

In a terminal:

gksudo gedit /etc/default/rcS

Look for this line: UTC=yes

Change it to: UTC=no

And save it:

Then set the time if it is wrong in System/Administration/Time and Date

Then either reboot or do this in a terminal:

sudo /etc/init.d/hwclock.sh restart

---

### Post by suomalainen on 2008-02-05
It works lfmoreno !!! Your the best!

---

