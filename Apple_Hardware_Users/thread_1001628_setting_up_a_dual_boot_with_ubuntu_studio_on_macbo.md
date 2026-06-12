---
title: "setting up a dual boot with ubuntu studio on macbook pro"
date: 2008-12-04
forum: Apple Hardware Users
---

### Post by Hume's doona on 2008-12-04
Hi,

I'm an ubuntu newby.

I've used Opensuse for a while through virtualisation.

I'm about to (hopefully in the next few days) set up ubuntu-studio as a dual boot on a macbook pro (mid 2008 model).

I have installed refIT as that seems the better option.

I mostly want to check for any driver incompatibilities with the ubuntu-studio kernel as opposed to the regular ubuntu kernel. Will any and all add-ons work from regular ubuntu repositories.

And if there's anything else that anyone knows and may be of use, let me know K?

cheers
Dan

---

### Post by cyberdork33 on 2008-12-04
It's worth a try, but there have been problems with the Ubuntu Studio kernel in the past. (Ubuntu Studio uses the realtime "-rt" kernel. It would often crash on Macs). You can, of course, download the Ubuntu Studio LiveCD and try running it on your Mac first to get an idea of how it works. The needed drivers and fixes should be compatible between Ubuntu and Ubuntu Studio though for the most part.

---

### Post by Hume's doona on 2008-12-04
> **cyberdork33 said:**
> It's worth a try, but there have been problems with the Ubuntu Studio kernel in the past. (Ubuntu Studio uses the realtime "-rt" kernel. It would often crash on Macs). You can, of course, download the Ubuntu Studio LiveCD and try running it on your Mac first to get an idea of how it works. The needed drivers and fixes should be compatible between Ubuntu and Ubuntu Studio though for the most part.

Thanks for that.

I have ordered the regular ubuntu as well as the studio version off ebay (too big a download for my connection).

I didn't think that studio was a live CD though? I was under the impression that it was text based install only. I guess I'll find out soon.

From what I have read of ubuntu, I should be able to configure a workable studio set up on the regular release anyway with a bit of work.

---

### Post by cyberdork33 on 2008-12-05
> **Hume's doona said:**
> I have ordered the regular ubuntu as well as the studio version off ebay (too big a download for my connection).
you can get a cd free from shipit ([https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)) Not Ubuntu Studio though.

> **Hume's doona said:**
> I didn't think that studio was a live CD though? I was under the impression that it was text based install only. I guess I'll find out soon.I actually don't know. I was assuming.

> **Hume's doona said:**
> From what I have read of ubuntu, I should be able to configure a workable studio set up on the regular release anyway with a bit of work.
I would think so. You could even set it up without the rt kernel if it is a problem.

---

### Post by _mario_ on 2008-12-06
> **Hume's doona said:**
> Hi,
I'm about to (hopefully in the next few days) set up ubuntu-studio as a dual boot on a macbook pro (mid 2008 model).

I mostly want to check for any driver incompatibilities with the ubuntu-studio kernel as opposed to the regular ubuntu kernel. Will any and all add-ons work from regular ubuntu repositories.

And if there's anything else that anyone knows and may be of use, let me know K?
yesterday, i installed the real-time kernel used by Ubuntu Studio on my MacBookPro 4. well, it works fine. no hardware/driver incompatibilities. all dkms packages from the mactel PPA do work as well. however, i observed a few drawbacks:
[LIST=1]
[*]the kernel doesn't use ACPI C-states lower than C1 (most likely to reduce interrupt latency). that causes the machine to consume more power (+5 W) while idling, effectively reducing battery time from 4.5-5 to 2.5-3 hours.
[*]suspend didn't work. for some reason the machine didn't switch off. i had to hard reboot.
[/LIST]

of course, as cyberdork33 wrote, you can convert every regular Ubuntu installation into Ubuntu Studio by installing:
[LIST=1]
[*]linux-rt - kernel with real-time patches. the 'traditional' Ubuntu kernel will work as well.
[*]ubuntustudio-audio/ubuntustudio-graphics/ubuntustudio-video - packages to install suggested applications for content creation. each application can also be installed manually.
[*]ubuntustudio-desktop - package to install desktop styles, themes, sounds, ...
[/LIST]

ciao,
Mario

---

