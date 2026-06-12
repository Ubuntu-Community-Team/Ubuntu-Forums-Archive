---
title: "[SOLVED] No Sound Devices Found After Update"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by gmjs on 2007-09-15
Hi,

I've just updated my Ubuntu 7.04 installation using the Update Manager and now Ubuntu cannot find a sound device on my system.

From memory, one of the updates was a newer kernel.  I now have the following kernel installed: 

[COLOR="Black"]2.6.20-16-generic[/COLOR]

I'm really new to configuring sound devices in Linux, as sound has generally never been a problem in most distributions I've tried.

Does anyone have any ideas on how I can get Ubuntu to recognise my sound device again, without downgrading the kernel header?

Many thanks,

Graham

---

### Post by gmjs on 2007-09-15
Sorry for being lazy!  Fixed now as follows:

Downloaded latest ALSA driver from alsa-project.org (1.0.14).

Installed using:

> ./configure
> make
> make install

Tested OK.

Hope this helps someone else if they have the same problem!

Thanks,

Graham

---

