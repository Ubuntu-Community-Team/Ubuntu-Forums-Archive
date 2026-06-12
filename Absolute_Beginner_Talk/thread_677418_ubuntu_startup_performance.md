---
title: "ubuntu startup performance"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-24
i was wondering if there is any general suggestions that could be given for improving the startup time in Ubuntu 7.10 like adding/removing applications, change system settings, changing items that load on startup, etc.  thanks.

---

### Post by Vadi on 2008-01-24
There are two "stages" - the before the login screen, and one after. Which are you interested in?

---

### Post by Paul820 on 2008-01-24
Go to System->Preferences->Sessions and uncheck what you don't need, like bluetooth or whatever. Or have a look here [http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

---

### Post by Matt26 on 2008-01-24
thanks for the suggestions- i think it would be the latter stage (after the login) screen as i have noticed that my desktop is taking a considerable amount of time to load up, more so than recently if i recall correctly- i just used Acronis True Image Server to make a disk-to-disk copy of my Ubuntu HD, as the original HD was failing- is it at all possible that the disk copy process could have had any impact on the startup performance?  thanks gain.

---

### Post by Vadi on 2008-01-24
No. Go to system - administration - sessions, and disable any things that you don't need - because after the login screen the bootup is very quick for me, max 7 seconds. You probably have too many applications launching.

---

### Post by Matt26 on 2008-01-24
i have added a few new apps since first installing Ubuntu (vmware, a couple of media players, email client, disk utility etc), so could these be impacting startup performance at all?  i'm not sure if any of them load up when the system boots or not.

---

### Post by sports fan Matt on 2008-01-24
Vadi,

Ater the login screen, are there any lists or posts in the forum as to which things can be disabled safely without crippling or corrupting a boot sequence so all these services arent running and it may increase the login to desktop from password stage?

---

### Post by emarkd on 2008-01-24
One service you may want to try disabling would be Tracker.  It's an indexer that makes searching for things in your home directory much faster, but it runs a lot to keep its database up to date.  If you don't use it, you can disable it and it may speed your system up a good bit.

As always, YMMV

---

### Post by Vadi on 2008-01-24
> **sox fan Matt said:**
> Vadi,

Ater the login screen, are there any lists or posts in the forum as to which things can be disabled safely without crippling or corrupting a boot sequence so all these services arent running and it may increase the login to desktop from password stage?

Sure. Here's what I went by:

[http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php](http://lifehacker.com/software/linux-tip/speed-up-ubuntu-boot-and-shutdown-process-267588.php)

Another one I found is here:

[http://knowledge76.com/index.php/Speed_Up_Boot](http://knowledge76.com/index.php/Speed_Up_Boot)

But I never used it, and from a quick look, doesn't look very well explained (some things are just said as "useless to me, I disabled it". So, unless you're sure you know what that thing does (google for it), or are convinced by the guide, don't touch it)

---

