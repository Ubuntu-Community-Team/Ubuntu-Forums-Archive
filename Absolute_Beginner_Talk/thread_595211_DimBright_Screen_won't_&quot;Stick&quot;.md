---
title: "Dim/Bright Screen won't &quot;Stick&quot;"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-10-28
Just upgraded last week to Gutsy but there is an odd behaviour of laptop LCD screen.  When I use the Fn up/down arrows to change brigthness, it won't stick with the new setting but will revert after a few seconds. (Dell 6400)  In Feisty, the dimming/brightening worked as you would expect and would stay with the new preset brightness.
Any ideas? Thanks.

---

### Post by carltondhouston on 2007-10-28
Me too.  HP DV6626US laptop.

LCD dims and brightens at random on battery power.  AC plugged in it seems fine.

I set to 20% dim instead of default 70%.  It still did it too much.

I went back in and the setting had magically changed to 25%.  I set it to not dim at all.

Seems like a bug to me.

---

### Post by strabes on 2007-10-28
System > Preferences > Power Management. Set the preferred brightness while on AC/Battery.

---

### Post by carltondhouston on 2007-10-28
> **strabes said:**
> System > Preferences > Power Management. Set the preferred brightness while on AC/Battery.
Thanks for the reply.

You may have missed some of the details of the posts you are replying to though.  When I tell my laptop to dim a certain amount due to running on battery, it will dim and brighten the LCD at random without any changes to power.  This all happened with a fully charged battery over the course of just a few minutes.

---

### Post by TuRfYMaN on 2007-10-29
> **flyingsolo said:**
> Just upgraded last week to Gutsy but there is an odd behaviour of laptop LCD screen.  When I use the Fn up/down arrows to change brigthness, it won't stick with the new setting but will revert after a few seconds. (Dell 6400)  In Feisty, the dimming/brightening worked as you would expect and would stay with the new preset brightness.
Any ideas? Thanks.

I'm experiencing the exact same problem with my e1505 Inspirion.  On battery operation, after sitting for a little while, the screen will dim.  I thought after I applied some input to it, it would come back from a dimmed state (similar to OSX), but it didn't.  I did find the place to adjust the brightness for the different power states, and those work. Also the function keys to turn the brightness up and down work once logged into GDM.  I guess the dimming is just a bug?

[EDIT]
Also, just to mention, I'm using the restricted driver (fglrx) for my ATI X1400 graphics device.

-Tom

---

### Post by inchaos on 2007-10-29
I've got the same problem on a Dell 1420n.

I'm sitting in lecture with my screen dimmed trying to conserve my battery and my screen keeps going back to 100% brightness without me touching anything.

Has anyone reported this bug on Launchpad yet?

---

### Post by inchaos on 2007-10-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/158343](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/158343) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've submitted a bug report.

PLEASE go to launchpad and confirm this/provide any additional information so we can get it fixed!

Thanks!

---

### Post by Inxsible on 2007-10-29
I see a similar problem but only when I run on battery. When on AC power, my screen does not change brightness.

When on battery power:
on inactivity, my screen goes dim, but when I move the mouse, brightness returns but not to what it was before. maybe just half way. I thought that was to conserve battery. But I guess I was wrong.

---

### Post by inchaos on 2007-10-29
Inxible: Mine does that as well.

I think I have about 4 things it's doing total, all on battery power.  The screen dimming feature works fine on A/C power.

You should add this to the bug report.  Every person that confirms it helps.

---

### Post by rebeldevel on 2008-01-19
I have the same problem. My laptop is a HP Compaq Presario dv6210br (V6000 series).

---

