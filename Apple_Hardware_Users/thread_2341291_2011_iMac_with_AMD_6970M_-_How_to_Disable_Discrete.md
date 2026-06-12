---
title: "2011 iMac with AMD 6970M - How to Disable Discrete GPU?"
date: 2016-10-26
forum: Apple Hardware Users
---

### Post by badowskiryan on 2016-10-26
I have a 2011 iMac 27" with a AMD 6970M (discrete) / Intel Graphics (integrated) hybrid GPU [[specs]("http://www.everymac.com/systems/apple/imac/specs/imac-core-i7-3.4-27-inch-aluminum-mid-2011-thunderbolt-specs.html")]. The AMD GPU has failed. I'm trying to disable it so I can get hardware acceleration with the integrated Intel GPU.

Ubuntu boots / installs only when I add "nomodeset" to GRUB. However, this disables hardware acceleration and forces software rendering mode -- with no brightness control. For three weeks, I've searched for a solution with no success.

I have tried all sorts of GRUB other options, including [this MacBook solution]("https://orville.thebennettproject.com/articles/installing-ubuntu-14-04-lts-on-a-2011-macbook-pro/"), but I always get a black screen after GRUB.

I have tried running 14.04 and installing AMD's proprietary fglrx drivers. This gets me to the login screen, but only the top 10 or so rows of pixels render. The rest of the screen is black or garbled.

I'm at a loss. Does anybody have advice for getting this system to work with the Intel GPU?

Or, if hardware acceleration is impossible, is there a way to enable brightness control while using nomodeset?

---

### Post by daftykins on 2016-10-30
Hi

My understanding was that this system was part of a class action lawsuit at some point and resulted in Apple giving refunds or replacement systems due to the ongoing graphics hardware issues. Whilst this isn't what you've asked, were you aware of this? It might be worth calling in to see whether any options still exist.

Onto the task at hand, if you felt comfortable or knew someone capable... I'm pretty sure the graphics board is modular and can be removed from the system leaving just the intact parts.

Failing that, a pastebin of your "dmesg" when booting a flash drive of say, 14.04.1 media, would be useful. Run:

dmesg | nc termbin.com 9999

Then share the resulting URL. At the same time:

cat /var/log/Xorg.0.log | nc termbin.com 9999

I've a feeling blacklisting the 'radeon' driver might help, but those logs should give some useful information.

---

### Post by dylanetaft on 2016-10-30
Check /sys/class/backlight for backlight devices.  You can echo stuff to brightness to see which device controls the brightness and go from there.

---

