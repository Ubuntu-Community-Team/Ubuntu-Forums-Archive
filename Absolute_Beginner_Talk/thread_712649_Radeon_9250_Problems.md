---
title: "Radeon 9250 Problems"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by christophicer on 2008-03-01
Installed Ubuntu 7.10. After a lengthy battle, i figured out to reset my bios to my onboard graphics chip. Ubuntu works we're all happy. Now i am trying to install my driver for my ATI radeon 9250 and I can't do it. I get the Xorg looking the exact same way as the posts do and it wont work, is it because i have to change my peripherals to my pci slot or what, i'm trying and trying and i just dont know because it all matches. i make sure i have the pci port right, everythings good. but it wont work unless i have it on onboard and everytime i install the driver for ati i have to reboot into recovery because my onboard wont support it and it freezes if i try to use the ati... any help would be greatly appreciated..


Acerpower SV
1 GB Ram
250 Gb HDD
ATI Radeon 9250 256 PCI
2.6 Intel Pentium 4 Overclocked to 3.2

---

### Post by Equinsu Ocha on 2008-03-01
You need to disable the onbaord video setting in BIOS, and the run;
```
dpkg-reconfigure xserver-xorg
```
from the recovery console. Once you can boot normally (xsession) using the ATI card, install the Envy package to obtain the best ATI driver.

ATI support is hit and miss, if this doesn't work post back here.

---

### Post by christophicer on 2008-03-01
have already tried that but it freezes in the recovery mode before i can get to the dpkg-reconfigure

---

