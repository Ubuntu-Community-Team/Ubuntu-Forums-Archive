---
title: "gdm user"
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by leatherworker on 2007-03-19
Hi there!

I upgraded this week with the regular upgrades that arrive and when I restarted my machine the next day, Gnome did not load - instead I got a message that said :

GDM user gdm does not exist, correct GDM and restart (exact message might be different) - I am using a different machine to post this)

Then in pressed Enter and got the command line prompt....

There I tried gdmsetup, but it said it could not open the display.

I had been running very successfully on Ubuntu for a few weeks before this....:confused: 

please help! I searched the web and this forum, but Do not find the correct help....

---

### Post by meborc on 2007-03-19
are you running edgy or feisty?

did you get a kernel upgrade? or did you see any packages removed by the upgrade?

can you boot to an older kernel from grub? or recovery mode and try "startx" from there?

also in recovery mode try "sudo apt-get update" and then "sudo apt-get install ubuntu-desktop" (so it is sure you have all the packages needed to run ubuntu)

...options are endless i'm afraid :p

---

### Post by leatherworker on 2007-03-19
> **meborc said:**
> are you running edgy or feisty?

did you get a kernel upgrade? or did you see any packages removed by the upgrade?

can you boot to an older kernel from grub? or recovery mode and try "startx" from there?

also in recovery mode try "sudo apt-get update" and then "sudo apt-get install ubuntu-desktop" (so it is sure you have all the packages needed to run ubuntu)

...options are endless i'm afraid :p

OK, I did all that successfully, but the problem is still there - 

I do not get the Gnome desk top - instead I get on a text-like screen the message:

"The GDM user 'gdm' does not exist.  Please correct GDM configuration and restart GDM"

How do I correct (edit) the GDM configuration?  I am running Edgy Eft

[Thanks for your help so far]

---

### Post by zvacet on 2007-03-20
```
gksudo gedit etc/gdm/gdm.conf
```

---

