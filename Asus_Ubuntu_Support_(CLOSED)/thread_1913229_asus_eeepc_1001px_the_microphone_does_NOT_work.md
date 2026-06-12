---
title: "asus eeepc 1001px: the microphone does NOT work"
date: 2012-01-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by escherichiarobi on 2012-01-22
hi everyone,
i'm pretty new and definitely need some help.
i just bought an asus eeepc 1001px with ubuntu 10.10 in it, but the microphone doesn't work, neither with the sound recorder program, nor with any other application as skype. i also tried to use an external one, but there is only one in/out jack, and the microphone is not recognized.
could you please help me? it's quite dire.
thank you very much

---

### Post by escherichiarobi on 2012-01-28
ok, a friend on mine saved my life founding this solution.

1) install alsa-hda-dkms according to
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

2) put options snd-hda-intel model=laptop-amic to /etc/modprobe.d/alsa-base.cont

it works, and i'm still with ubuntu 11.04 btw.

hope it'll be helpful

---

