---
title: "clamshell woes"
date: 2006-08-14
forum: Apple PPC Users
---

### Post by nilcam on 2006-08-14
after several tries, i was able to complete the install of Xubuntu 6.06.1 on a tangerine clamshell iBook. the system boots up, but after login the screen gets wacky. it's not split, but the top part of it is scrambled and moving a window or the cursor causes more parts of the screen to become scrambled. i searched the forums and found a topic that said to edit the xorg.conf file to define the horizontal and vertical information in the video description. when i opened xorg.conf and checked the video description, these variables were nowhere to be found. the video card was properly described in the file. :confused:  any ideas?

thanks.

---

### Post by Peter76 on 2006-08-14
Hit ctrl+alt+f1; you should get a login prompt. Login and type:

sudo dpkg-reconfigure xserver-xorg

Good luck

---

### Post by nilcam on 2006-08-14
thanks for the suggestion. i went through the process but am still having the same problem. i tried to boot from the xubuntu live cd and everything ran fine. i decided to do a fresh install from that cd, but the installer crashed everytime i launched it.

the problem seems to be refresh rate related. if i mouse over a part of the screen that is scrambled, that part clears up. i've checked apple and everymac.com, but cannot find the refresh rate on the first generation iBooks. does anyone know?

---

