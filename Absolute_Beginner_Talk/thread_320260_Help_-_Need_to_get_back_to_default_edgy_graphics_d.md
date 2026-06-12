---
title: "Help - Need to get back to default edgy graphics driver"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by mickeythecat on 2006-12-17
Now starting from live CD so obviously I have to fix a major problem.

I tried to install the linux ATI 9250 graphics driver from the ATI website. In the process I must have set something wrong in their menu system.  Upon restart I get a pure black screen - thus I am dead in the water.

I tried to start in safe mode (which I can) and moved any created files in /usr and below to filename.old to try and disable them - did not work.  New to linux and am really have no ideas how or where graphics drivers are set or stored.

How do I get back to the default ubuntu edgy graphics driver???

Thanks.

---

### Post by mickeythecat on 2006-12-17
OK was able to recover.  From searching on this board, found out that /etc/X11/xorg.conf file is critical.  The ATI graphics driver installation program fortunately made a backup of this file so i was able to copy that one to xorg.conf.

---

