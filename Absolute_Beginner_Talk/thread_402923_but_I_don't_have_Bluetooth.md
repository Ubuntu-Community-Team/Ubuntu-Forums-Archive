---
title: "but I don't have Bluetooth"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-04-06
about 15 mins ago, my comper locked up, so I rebooted and took a look at the logs to see if I could figure anything out (which I can't), anyway, I noticed several msgs in my syslog referring to bluetooth. I don't have any bluetooth devices.... How do I trun it off if it is indeed running?:confused: :confused: :confused: :confused: :confused:

---

### Post by wesley_of_course on 2007-04-06
Wesley here ;


         $ sudo apt-get install sysv-rc-conf
  
                  is one way and System - Administration - Services is another .


        Good Luck  and don't turn off 2 many " Services " or ,,,,,,,,,,,,,,,,, !

     You'll have a busy weekend !

---

### Post by yabbadabbadont on 2007-04-06
Or you could edit the bluetooth config file in /etc/default and configure it to not start.  You could also remove all the bluetooth packages although that will probably remove ubuntu-desktop.  That isn't a big deal as long as you are not planning on using the update-manager to upgrade from one version of Ubuntu to the next any time soon (i.e. from Edgy to Feisty)

---

