---
title: "ubuntu causing hard drive failure"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-11-01
I forget the link but was hearing the ubuntu was causing hard drive crashes for laptops and now not sure if i want to put ubuntu on my laptop.  Any info on this.

---

### Post by Crafty Kisses on 2007-11-01
> **RyanZec said:**
> I forget the link but was hearing the ubuntu was causing hard drive crashes for laptops and now not sure if i want to put ubuntu on my laptop.  Any info on this.

I've had Ubuntu on my laptop for about a year now, I haven't had any problems. :)

---

### Post by Jimmyfj on 2007-11-01
I have installed Ubuntu on several laptops and have never seen Ubuntu crash a hard drive in any way before. I just need to ask you: Do you mean by way of destroying an existing Windows or physically destroying the drive? This sounds like a FUD story to me.

---

### Post by Hospadar on 2007-11-01
There is a known issue with ubuntu on some hard drives.  It has to do with the sata drivers and some power management tools.  Sometimes it causes laptops to spin up a lot more than they should.  You can do a couple things:
A) google around and find out if your machine is affected
B) turn off the power management features in Systems->Preferences->Sessions and System->Administration->Services

turning off the power management might give you less battery life on your machine, and you wouldn't get the battery info, but if your machine is usually plugged in, thats not so important anyways.

In general, you will probably be just fine.  Just keep an eye (or ear) on your hard drive and see if it is constantly spinning, and check to see if your laptop would be affected.

---

### Post by kefurd06 on 2008-01-21
i read about this problem here:

[http://linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear)
[http://linux-hero.com/rant/ubuntu-hard-drive-explosions](http://linux-hero.com/rant/ubuntu-hard-drive-explosions)

the short is this: the problem results from laptop-mode, which is disabled by default, at least in gutsy (7.10). if you are worried that you might be affected, run this:

```

grep ENABLE_LAPTOP_MODE /etc/default/acpi-support

```
if the system returns TRUE, you need to change your laptop-mode configuration settings. if it returns FALSE, ur fine. if you're worried u might some day turn on apm, u can go ahead and change the setting. see the second link above for instructions on how to do this.

---

