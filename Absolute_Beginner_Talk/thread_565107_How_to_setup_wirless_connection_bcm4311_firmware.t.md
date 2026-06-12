---
title: "How to setup wirless connection bcm4311_firmware.tar.bz2"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by open-gl on 2007-10-01
I downloaded bcm4311_firmware.tar.bz2
step 1 - open a terminal and type: tar -xjvf bcm4311_firmware.tar.bz2
step 2 - sudo mv bcm43xx* /lib/firmware 
step 3 - sudo modprobe bcm43xx
step 4 - gksu gedit /etc/modules
step 5 - a typed in bcm43xx in modules and clicked save
step 6 - sudo iwconfig eth1 essid [network name]
step 7 - sudo iwconfig eth1 key [wep key]
step 8 - sudo dhclient3 eth1

Did I do everything correct or not.

---

### Post by j.bunce on 2007-10-02
sudo ifup eth1

---

