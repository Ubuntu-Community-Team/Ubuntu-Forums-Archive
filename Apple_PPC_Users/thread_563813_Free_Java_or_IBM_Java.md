---
title: "Free Java or IBM Java?"
date: 2007-09-30
forum: Apple PPC Users
---

### Post by mbechdel on 2007-09-30
Hello all,

Just installed xubuntu on a G4 Powerbook. I just wanted your opinions on which to use, GCJ or IBM Java? My class is building a Java application that creates 2D/3D objects. We are using the Java3D Utils package. So if any of you have any experience with this please post.

EDIT: Removed Free Java, I have IBM Java now. I can run Applets and everything fine. Although when I run BlueJ I am getting this error message: "Bluej was unable to create a virtual machine(VM) to execute projects". BlueJ has a FAQ on this; however, it says it is related to my Firewall settings most likely. Although, to my understanding xubuntu/ubuntu doesn't have a Firewall by default.

Searching it looks like it might have something to do with my loopback/localhost settings. My /etc/network/interfaces file has this in it:

--------------------start of file

auto lo
iface lo inet loopback


iface eth1 inet dhcp
wireless-essid uninc
wireless-key 1313131313

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---------------------end of file
Thanks,
Max

---

### Post by idkwot on 2007-10-01
i would go with GCJ

---

