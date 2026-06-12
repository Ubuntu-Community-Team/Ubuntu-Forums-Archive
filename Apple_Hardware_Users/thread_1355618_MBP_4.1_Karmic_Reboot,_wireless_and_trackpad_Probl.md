---
title: "MBP 4.1 Karmic Reboot, wireless and trackpad Problems"
date: 2009-12-15
forum: Apple Hardware Users
---

### Post by kylegray on 2009-12-15
I have installed Karmic on my Macbook Pro(4.1) by using boot camp (no refit) along side OS X 10.6.2. 

my initial problem was with the the wireless Broadcom driver, i connected via land line and installed all the updates but when i went to activate the driver it would load and then it would not activate. i manually installed the Broadcom STA wireless driver through the terminal by creating a directory(hybrid_wl), black listed ssb, ect. ect. After this Ubuntu recognized my wireless and found the connection. 

Second i made some alterations to my Trackpad to disable tapping and to enable two finger schrolling and three finger clicking by editing(or creating?) my fdi preferences in the terminal. However this required me to reboot for it to take effect. 

Now (sorry for all the preliminary) this brings me to my current issue, when i reboot (hold down alt botton and choose my ubuntu partition) my system loses all the fixes i had just applied! so now i have no wireless internet, still cant "activate" the Broadcom driver (however i was able to activate my graphic driver), and my trackpad is still default...

I only have one user so i can't see it being a root problem, i used sudo for tasks that were prohibited or denied such as blacklisting the contradictory drivers for wireless. maybe it has something to do with Grub and how it boots? (always asks me what i want to boot after i hold down option and select my Ubuntu partition), i really have no idea, if anyone can help me out with this problem i would be forever grateful (it's keeping me up at night!)

---

### Post by linuxopjemac on 2009-12-15
interesting link for you, but I guess it's outdated for Karmic.
[https://help.ubuntu.com/community/MacBookPro_Penryn](https://help.ubuntu.com/community/MacBookPro_Penryn)

---

### Post by kylegray on 2009-12-15
Thanks for the reply, for now i think i will try reinstalling with Jaunty Jackalope 9.04 and follow the instruction of [this link]("https://help.ubuntu.com/community/MacBookPro4-1/Jaunty"), since it seems to be more up to date. Sucks that i have to run an older version of ubuntu... not the harmony i expected from Ubuntu, but still infinitely greater than that Microsoft OS.

---

