---
title: "trying to install Lubuntu 12.10 on iMac G5 iSight - hard disk invisible"
date: 2013-06-22
forum: Apple Hardware Users
---

### Post by jtreml60 on 2013-06-22
Hi, I'm now very close to taking a hammer to my G5 iSight so desperate for any advice. The hard drive and PSU were faulty and both have now been replaced. The superdrive also only boots from CDs not DVDs so I was heading down the Ubuntu route to at least get an OS on it (only have Tiger or Leopard on retail DVDs). I can boot into open firmware and boot off ubuntu on a USB stick but the installer and GPARTED cannot see the hard disk. I know this hd is fine as have tested it on a PC, created and deleted partitions and volumes no problem, and have also tested the SATA cable in the iMac. using open firmware, it looks like it thinks there is a disk there on the sata controller (using dev / ls and devalias). I've also tried reset PRAM and SMU but no good. other than that, iMAc seems OK - ie can boot to Ubuntu from the USB stick, but when run the partition editor it cant see the internal hard disk at all. I've also had the logic board out and checked all capacitors for signs of leakage etc and anything else that might cause an issue. Now come to a dead end. Anyone got any ideas of what I could try next?

---

### Post by jtreml60 on 2013-06-24
all resolved - issue related to SATA interface speed of the disk - new hard disk supported 6GB/s but needed to drop down to 1.5GB/s to work in this system

---

