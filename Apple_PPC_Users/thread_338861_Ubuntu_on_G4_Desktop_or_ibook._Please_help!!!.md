---
title: "Ubuntu on G4 Desktop or ibook. Please help!!!"
date: 2007-01-15
forum: Apple PPC Users
---

### Post by dhoffer on 2007-01-15
i have successfully install Ubuntu on an internal IDE drive via the CD (6.10) but can't get past the screen that asks me to choose "l" to boot into Linux. My G4 tower (and all other macs) keeps going back to the "choose startup drive" as in "if you hold down the option key at startup". i have a Dual Processor 500mhz G4. i have also tried to boot with this drive via firewire on this machine as well as my iBook G4 (firewire) and PB pismo (firewire). am i doing something wrong? Please help!!!

---

### Post by didg on 2007-01-15
No you aren't but at least yaboot install didn't fully succeed. Or did you move the disk?

If you know the boot partition number. you can try to boot from the OF console.
with something like 
boot hd:9,\\yaboot
if it's the first IDE disk.

Or boot with the liveCD, find the boot and root partition and change /etc/yaboot.conf.
and rerun ybin.

---

