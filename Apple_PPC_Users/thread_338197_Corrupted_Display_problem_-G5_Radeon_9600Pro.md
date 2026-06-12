---
title: "Corrupted Display problem -G5 Radeon 9600Pro"
date: 2007-01-14
forum: Apple PPC Users
---

### Post by zeigerpuppy on 2007-01-14
I have just tried Ubuntu 6.10 on my G5 Dual 2GHz, with Radeon 9600 Pro
and Cinema Display 23" (ADC connector, old model with white surround)
Unfortunately, I get corrupted display on the console and X
I figure it must be the ati driver?
Everything else works fine.

The display produces random red pixels flashing all over the place and looks like it loses sync occasionally, in X the flashing pixels are less obvious (but still there, obscured by the background)  If I change screen resolution, the display is corrupted (lines superimposed all over the place) which can be kind of reset by switching to the console and back.

Could this be just an xorg config problem or do I need to play around with the driver?

Thanks

PS: the display works perfectly in OS X

---

### Post by amadain on 2007-01-14
Hi,

I have almost the same configuration (I recently upgraded to Feisty though - but 6.1 worked perfectly before).

I attach my xorg.conf file.

I hope that you find it useful. If necessary I can also attach my log file.

---

