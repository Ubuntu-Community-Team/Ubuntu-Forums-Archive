---
title: "wireless in Lucid on MacBook Pro 5.1"
date: 2010-10-09
forum: Apple Hardware Users
---

### Post by nokangaroo on 2010-10-09
Does anybody know how to enable wireless for Lucid on a mbp 5.1? I tried everything I could find, including ndiswrapper, fw-cutter and installing the broadcom driver from source, and nothing works. The bcmwl kernel source seems to create a kill file in etc/modprobe.d that I can't get rid of, which blacklists everything. Other people must have the same problem, but I can't seem to find any useful information. Can somebody help me please? Wireless on Mac OS works so this is not a hardware problem. The output of iwconfig is    lo        no wireless extensions.   eth0      no wireless extensions.     pan0      no wireless extensions.    which is *bad*. I am using 2.6.32-25-generic-pae but I have the same problems with the standard kernel.

---

### Post by inphektion on 2010-10-09
I have a macbook pro 5,2.
I installed the broadcom sta drivers that popped up in the restricted drivers.

then wifi was "on" but i couldn't connect to any wpa networks.
using the 3 packages from comment #35 here: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/572777)
seems to have resolved that for me for now.  Hopefully something better comes around cause wireless performance seems bad compared to when i boot into macos.

---

### Post by gordintoronto on 2010-10-09
Use a wired connection, then run Hardware Drivers. You might need to get rid of all the things you tried, first.

---

