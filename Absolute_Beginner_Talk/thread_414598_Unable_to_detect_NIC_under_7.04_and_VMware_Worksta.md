---
title: "Unable to detect NIC under 7.04 and VMware Workstation 5.5.3"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by AncientPC on 2007-04-20
Title says it all, network is bridged under VMware Workstation 5.5.3 and was working under Ubuntu 6.10.  I did a clean install of 7.04 and Administration -> Network doesn't list any NIC.

---

### Post by SittingCrow on 2007-04-20
same sh.t for me

---

### Post by fishwithapipe on 2007-04-20
get the latest version of vmware-any-any-update from

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz)

untar and run runme.pl

this update fixes compatibility with .20 kernels, you will need at least kernel headers and build-essential installed i cant say what else exactly as i already have them, goodluck.

---

