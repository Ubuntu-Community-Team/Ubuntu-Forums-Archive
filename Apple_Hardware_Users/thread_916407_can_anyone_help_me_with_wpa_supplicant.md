---
title: "can anyone help me with wpa_supplicant"
date: 2008-09-10
forum: Apple Hardware Users
---

### Post by kylegio on 2008-09-10
so last time i tried to install wpa_supplicant it got all messed up, not only did it not work but it also stopped my ethernet connection from working either. i tried following walkthroughs and stuff but to no avail, does anyone know where i can find some better info on how to do it. i would rate my ability in the area as fairly novice, im comfortable in linux but know very little about wpa_supplicant and network configuration in linux.

as it is right now i am running ndiswrapper  (sucsessfully) for my macbook, i can scan and see the networks but can not connect. (because they are all protected)

my network uses 
wpa-tkip
PEAP authentication
EAP-MSCHAP V2

and i have a login username and password, when connecting in windows a little popup comes up asking for username and password, i dont ever enter a pass key or anything for the network, and 99% of the things i could find online all handled that type of setup


can anyone help? i can SURVIVE without it but id rather have it, and do not want to risk messing up my wired connection again

thanks
kyle

---

### Post by vikram on 2008-09-10
this worked for me
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/Kubuntu)

---

### Post by kylegio on 2008-09-11
unfortunatly like all the other how-to's i found it doesnt really talk about the type of authentication i need

---

### Post by cyberdork33 on 2008-09-11
> **kylegio said:**
> unfortunatly like all the other how-to's i found it doesnt really talk about the type of authentication i need

Well, you do have some unique authentication requirements. (Uncommon here anyway).

You do not need to install wpa_supplicant. The issue likely lies in the fact that ndiswrapper has some issue with WPA encryption right now. Do you have a Broadcom card? You can try to use the wl driver. It seems to work better.
[http://ubuntuforums.org/showthread.php?t=914697](http://ubuntuforums.org/showthread.php?t=914697)

---

### Post by hajk on 2008-09-11
I've found this older thread, [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=202834](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=202834), helpful.

---

