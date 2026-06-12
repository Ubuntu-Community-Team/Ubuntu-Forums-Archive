---
title: "[SOLVED] which is easier to get above 800x600"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by armandh on 2007-07-29
new to ubuntu and trying it on several old machimes
of 3 machines running Ubuntu one gets above 800x600 after install the other two seem to be installed missing the needed ??? of the two that wont get above 800x600 one is an on board i810 chip the other a PNY card with a nvidia 2 chip [I think]

I know the i810 chip can be forced 1024x768  in the boot up with some live disks
what do  I need?
would it be easier to look for a different card v the pny/nvidia2 odd ball?

---

### Post by armandh on 2007-07-29
my second successful command line instruction found searching this topic

this did it
sudo dpkg-reconfigure -phigh xserver-xorg

---

