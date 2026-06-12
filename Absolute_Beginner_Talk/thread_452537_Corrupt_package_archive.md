---
title: "Corrupt package archive"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Whatever6750 on 2007-05-23
When I go to update I get an error saying, 

E: /var/cache/apt/archives/tzdata_2007e-0ubuntu0.7.04_all.deb:
Corrupted filesystem tarfile - corrupted package archive

This has happened on about 4 installs. Ive tried two different downloads / burns of the regular live CD and the alternative all do the same thing. Its happening right after install then trying to update, i.e. I haven't done anything after the install but try to update.

Anyone have any ideas?

---

### Post by dstew on 2007-05-23
Maybe it is a corrupted package archive file. You can delete the package file```
sudo rm /var/cache/apt/archives/tzdata_2007e-0ubuntu0.7.04_all.deb
```, then re-install it from synaptic. Then try the update. The package is the Time Zone and Daylight Saving Time Data package, for your info. Nothing critical.

---

### Post by Whatever6750 on 2007-05-23
> **dstew said:**
> Maybe it is a corrupted package archive file. You can delete the package file```
sudo rm /var/cache/apt/archives/tzdata_2007e-0ubuntu0.7.04_all.deb
```, then re-install it from synaptic. Then try the update. The package is the Time Zone and Daylight Saving Time Data package, for your info. Nothing critical.

I tried that last time with any archive packages that where reported as corrupt and ended up just really messing up ubuntu and had to reinstall which is where I'm at now. Even after I had deleted the packages it would still say the same ones where corrupt...

This has happened on 4 recent installs so I don't think its as simple as a corrupt archive package that needs to be replaced..

---

### Post by Whatever6750 on 2007-05-24
I tried going from 6.10 to 7.04 and get the same thing, Now I have 16 broken packages and synaptic cant fix them. Its got to be happening with update....

---

