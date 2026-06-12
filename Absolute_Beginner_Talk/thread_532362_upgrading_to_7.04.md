---
title: "upgrading to 7.04"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by JamesA on 2007-08-22
Hey Everyone,

Having problems upgrading to ubuntu 7.04.

When i click 'upgrade' on the update manager, it stalls at 60% then tells me it "could not download all repository indexes"

```
ttp://compiz-mirror.lupine.me.uk/dists/edgy/Release.gpg: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/i18n/Translation-en_US.bz2: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy-amd64/i18n/Translation-en_US.bz2: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/i18n/Translation-en_US.bz2: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy-amd64/i18n/Translation-en_US.bz2: Could not resolve 'compiz-mirror.lupine.me.uk'
http://amaranth.selfip.com/dists/edgy/Release.gpg
http://amaranth.selfip.com/dists/edgy/lrm/i18n/Translation-en_US.bz2
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/binary-amd64/Packages.gz: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy-amd64/binary-amd64/Packages.gz: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy/binary-amd64/Packages.gz: Could not resolve 'compiz-mirror.lupine.me.uk'
http://compiz-mirror.lupine.me.uk/dists/edgy/main-edgy-amd64/binary-amd64/Packages.gz: Could not resolve 'compiz-mirror.lupine.me.uk'

```

---

### Post by annda on 2007-08-22
disable all edgy repositories in system>administration>software sources (if it exists in edgy, otherwise in synaptic) and you should be fine.

---

### Post by linuxwizard on 2007-08-22
Also when upgrading it is recommended that you remove or disable any extra repository that may have been added besides the Ubuntu repositories.

---

### Post by JamesA on 2007-08-22
Thanks guys, seems to be working now.

---

