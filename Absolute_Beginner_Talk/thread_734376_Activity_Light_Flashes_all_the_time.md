---
title: "Activity Light Flashes all the time"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2008-03-24
I've noticed that my amber activity light is flashing every 6 to 10 seconds or so
and was wondering if this is normal? Even when I am not doing anything on the
machine it still does this.  I did add the System Monitor to my top panel beside my time,
could that be causing the activity? 

I have 1 Gig of DDR ram and set up a 1 Gig Swap partition.

Just would like to know if the activity light should be doing that...... Thanks.....

---

### Post by Sam Lars on 2008-03-24
Mine does the same thing, it's just routine disk access.

---

### Post by Orbital75 on 2008-03-25
Ah........ That makes me feel better then.  :)
now days you really have to be careful and
every time that light would blink, I'd get paranoid.
Thanks for relieving me.... :)

---

### Post by Whiffle on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Is it your hard drive light, and is this on a laptop?  You may the load_cycle_count issue.  An easy way to check is to do

sudo hdparm -B255 /dev/whatever/your/hard/drive/is

and see if it stops.  If it does stop, then you've probably  got it.

---

### Post by Orbital75 on 2008-03-26
Well, it's on a Desktop and yes it is the Harddrive light so it could be this.
What does everyone else think, possible?

---

