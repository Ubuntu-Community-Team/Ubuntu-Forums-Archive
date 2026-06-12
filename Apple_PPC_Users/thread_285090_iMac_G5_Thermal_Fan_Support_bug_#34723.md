---
title: "iMac G5 Thermal Fan Support bug #34723"
date: 2006-10-26
forum: Apple PPC Users
---

### Post by RoadTripDK on 2006-10-26
With regards to the iMac G5 Thermal Fan Support bug #34723, there was a manual solution posted:

# As root, type:
```
apt-get install powernowd
cd /lib/modules/$(uname -r)/kernel/drivers/macintosh
ls | cut -d. -f1 | xargs -n1 modprobe

lsmod | cut -d" " -f1 | grep windfarm >> /etc/modules
```

Can anyone tell me "apt-get install powernowd" also work on G5 single (PowerMac 9.1) boxes? Will this also work with Dapper? I am having problems with the new Edgy CDs failing validation and was going to try a Dapper install.

---

### Post by stmiller on 2006-10-26
[http://ubuntuforums.org/showthread.php?t=284508](http://ubuntuforums.org/showthread.php?t=284508)

---

