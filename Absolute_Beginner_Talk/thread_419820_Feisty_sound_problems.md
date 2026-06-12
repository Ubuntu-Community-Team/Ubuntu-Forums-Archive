---
title: "Feisty sound problems"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by willbur on 2007-04-23
Hello everyone

I have an IBM T40 which had a working Edgy installation on it. I upgraded to Feisty via a fresh format and install.

When I perform a normal startup, I get sound. After a hibernate, sound disappears and will not work after a subsequent restart. However, if I perform a full shutdown and startup, sound works again!

I've looked on the forums and tried the 'muting of headphone and line-in in alsa-mixer' fix mentioned elsewhere (sorry - I can't find it again!) but no joy. I'm sure this is something simple, but I'm enough of a newbie to be completely stumped. Does anyone have any ideas?

Many thanks in advance ladies and gents

willbur

---

### Post by leibowitz on 2007-04-23
I don't think it's so simple. ACPI is an headache for the kernel and the drivers. They do not talk nicely between them after a resume. Maybe you have to check acpi options or something related to it. Sorry I can't help you to do this.

---

### Post by willbur on 2007-04-24
leibowitz - thanks for taking the trouble to reply. It's not a big problem and I can easily work around it. It's just a shame that my computer seems to be far more compatible with Edgy :neutral:

Thanks again...

---

### Post by mjukis on 2007-04-25
I have a IBM X40 and have the exact same problems. Found serveral IBM/Lenovo users in the forum with this problem but no solution yet...

---

