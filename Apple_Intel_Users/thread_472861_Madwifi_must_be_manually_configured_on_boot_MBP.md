---
title: "Madwifi must be manually configured on boot MBP"
date: 2007-06-13
forum: Apple Intel Users
---

### Post by heroinhero on 2007-06-13
Well, I managed to get X running and mostly everything set up, but the wireless is still a problem for me.  I could not get madwifi to load from the restricted modules, so I ended up building it myself.

After building and installing, it works as it should.  But a new ath0 entry doesnt appear in the gnome network manager, and everytime on boot, I need to do

sudo iwconfig essid "dd-wrt"
sudo dhclient ath0

Is there any way that I can automate this so that I do not need to open up terminal on boot everytime? 

Btw, I have tried to add a script into /etc/init.d/ to do those commands, but they do not work as intended.

---

### Post by LeopoldBloom on 2007-11-06
Have you tried adding it to System-->Preferences-->Sessions-->Startup Programs?

---

