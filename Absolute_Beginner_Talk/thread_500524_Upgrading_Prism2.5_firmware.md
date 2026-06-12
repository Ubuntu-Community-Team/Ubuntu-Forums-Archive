---
title: "Upgrading Prism2.5 firmware"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by remeron on 2007-07-14
HI there, I've just installed ubuntu and linux for the first time and i'm loving it....been tinkering with it day and night.  I've got a Presario 2100 and the wifi is running Prism 2.5 station firmware v1.4.9
I'm trying to upgrade the frimware to v1.7.4 as i heard that the newest firmware supports WPA encryption.  I've downloaded hostap-utils 0.4.0 and installed

i'm running into trouble when i try to flash the latest firmware (yes, i checked, i downloaded the correct firmware), but whenever i use

prism2_srec -v -f wifi0 <primary firmware> <station firmware> 

i get an error saying 

"Could not read wlan PDA. This requires PRISM2_DOWNLOAD_SUPPORT definition in driver/module/hostap_config.h

I don't know what that means.  And i can't even find that hostap_config.h 

Plsease help.

---

