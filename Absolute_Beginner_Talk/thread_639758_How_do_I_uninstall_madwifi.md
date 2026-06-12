---
title: "How do I uninstall madwifi?"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by SpinningAround on 2007-12-13
I'm following this guide [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo) and have come to this part

> 
cd scripts
./madwifi-unload.bash
./find-madwifi-modules.sh $(uname -r)
cd ..


Problem is that is search for madwifi and found this "/lib/modules/2.6.22-14-generic"
but there is no map called scripts or any of the files. or i might have missed them with search function. (hidden files was included)

I followed this [http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu) so I have disabled ath_hal

Should i proceed with the installation?

---

### Post by Dapman01 on 2007-12-13
Why do you want to get rid of madwifi

---

### Post by SpinningAround on 2007-12-13
> **Dapman01 said:**
> Why do you want to get rid of madwifi

The guide say that i need to remove the old drivers to get the new one to work. I need the newest driver since my card got supported in that one.

---

### Post by Dapman01 on 2007-12-13
Just go to the synoptic and type in madwifi, it's going to be the restricted drivers.  uninstall those but what are you trying to do, If you are trying to get wifi, you need to download wifi radar and it will find any available wifi in your area

---

