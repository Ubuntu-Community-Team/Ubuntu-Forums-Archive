---
title: "[SOLVED] ATI Restricted Drivers on Ubuntu 7.10 Gutsy"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by gecko on 2007-10-23
When you have an ATI card you need to install restricted video drivers. The default repositories enabled with a new install of Ubuntu desktop edition do not allow the installation of these drivers. 

If you have tried to install without enabling the extra repositories it will say the package xorg-driver-fglrx is required. When you try to install this package you will get a failed dependancy for libstdc++5. You do not need to resolve the libstdc++5 dependency if you add the additional repositories outlined below.

Click Systems -> Administration -> Software Sources
Tick the first, third and last option in the list then click ok.
Click reload (requires internet connection) to refresh the available package list.

Now you can install the restricted ATI video drivers.

Click System -> Administration -> Restricted Drivers Manager
Tick the ATI Accelerated Graphics Driver then click ok.

The drivers should load and install. A reboot is required to activate the drivers. This solution was tested on an LG P1 Express Dual Laptop with ATI Mobility Radeon X1400 Video Card. 

If this solution worked for you, please report you results in reply to this post. Feedback/Suggestions for improving this solution are always welcome.

Regards

Kevin

---

