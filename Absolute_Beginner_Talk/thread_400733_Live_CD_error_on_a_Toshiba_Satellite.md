---
title: "Live CD error on a Toshiba Satellite"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by zzRider on 2007-04-03
I am trying to run a Live CD of Ubuntu on my Toshiba Satellite P105-S6147 and I keep getting this error:

(warning) I810: No matching Device section for instance (BusID PCI : 0 : 2 : 1)
(error) No video BIOS mode for chosen depth.
(error) Screen's found, but none have a usuable configuration.
Fatal server error
no screens found.
<ok>

Now in the boot section I have tried this:
Boot: live vga=771 noapic nolapic
Boot: live fb=false
Boot: live intel fb800

No luck... any suggestions?

---

### Post by dbbolton on 2007-04-05
did you check the md5sum on the iso before burning it ?

---

