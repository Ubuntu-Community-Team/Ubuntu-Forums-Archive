---
title: "My ibook don't suspend...."
date: 2005-12-09
forum: Apple PPC Users
---

### Post by lqbweb on 2005-12-09
Hi

I've one issue with my ibook G4 800 (dual usb).

At begining of install Kubuntu, the computer go to suspend perfect when I close the screen... but I don't know what i made but now the computer don't suspend....

When I close the screen now, the computer make no thing.... no try to suspend, nothing.... I don't touch any configuration of apm or power or acpi.....

I tried to load Kubuntu live cd and compare /etc/power and /etc/apm with my installation.... and there are no differ....

Anyonw know what can I make?

Thanks

---

### Post by hatefulthreatening on 2005-12-11
The macs tend to use pbuttonsd for the power management stuff.


Try installing powerprefs(apt-get install powerprefs).

Run that as root and see if you configure your power saving options.

---

