---
title: "remote desktop Windows to Linux"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by akkad on 2007-09-19
actually i have a mobile device with windows mobile 6 platform (wish to have ubuntu platform one day) , where from my mobile i can successfully connect remotely to a windows pc via a remote desktop client application installed on my mobile, is it possible to connect to ubuntu linux via the same application cuz i tried to do it but it is useless, i have enabled remote desktop from preferences >>> remote desktop  but still useless,  any idea ??

---

### Post by KevinD_Atl on 2007-09-19
I do it just fine using VNC.  I think that remote desktop in Ubuntu uses the VNC protocol type.

Test it out with a differnt box other than the mobile with VNC viewer on the local intranet. If that works, see if you can get VNC viewer on your mobile.

Outside the intranet, you'll need to forward the port to that IP of the ubuntu machine.  Default is 5900.

---

