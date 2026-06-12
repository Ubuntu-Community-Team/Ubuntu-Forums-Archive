---
title: "problem with the display of kubuntu 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by dtzxdtzx on 2007-05-13
Hi,

After hesitating for 2 weeks, I finally installed kubuntu on my ibm a21p notebook. However, the display is divided into two parts. The left part is about 2/3 of the display and the right part is about 1/3 of the display. I also have two mouse icons. When I move and click the mouse, both of them will move to the same place and been clicked. The video card is ATI Mobility-128. Can anyone help me to solve this problem? Otherwise I could not use the linux just installed since the display is really messy.

Thanks

Frank

---

### Post by dtzxdtzx on 2007-05-13
After I installed the kubuntu and reboot the machine, my display becomes even worse than installation process. I could not login the machine since I could not see any prompt for username and password. The screen is all most blank. What should I do?

Thanks

Frank

---

### Post by zvacet on 2007-05-13
Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

select **vesa** driver and when you get graphic go and search proper drivers

---

### Post by dtzxdtzx on 2007-05-13
How to boot in recovery mode?

Thanks

Frank

---

### Post by dtzxdtzx on 2007-05-14
Hi, 

I got the recovery mode and select the vesa mode. Now I can get graphic, the graphic is small screen on 15 inch display. How can I get the correct driver for this machine? It is ibm A21p with ATI mobility 128 graphic card.

Thanks

fRank

---

### Post by pikul on 2007-05-14
You need to install the correct ati driver, i dont know about kubuntu, but on ubuntu what you do is go to System - Administration - Restricted Drivers Manager and select it :)  thats the easy way.

---

