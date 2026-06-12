---
title: "Wi-Fi help"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2008-01-18
Okay guys my Wi-Fi to my ubuntu laptop has been going fine until recently when i tried to connect it goes through like it's about to connect then prompts me to enter my WEP password, so I do and the same thing happens all over again. I have no idea on what I should do. It has been bugging me for almost two weeks now. Please someone help me out. I'm pretty sure it's not my wireless card because I was able to connect to my friends unsecured network and my jobs protected Wi-Fi. Just not my homes. Any ideas?:confused:

---

### Post by tennvolsmb on 2008-01-18
Anyone willing to share. I'm really lost on this.

---

### Post by ugm6hr on 2008-01-18
Just to show people are reading...

Can you connect from other wifi devices to your home network?  Have you changed any of the settings?  Do you use MAC filtering?

My suggestion would be to change your home network to unsecured, and reconnect to make sure there is no problem.  Then put WEP back up with a new HEX password, and use that.  Network Manager sometimes misbehaves with ASCII passcodes.

Afraid I have no other explanations why it would be misbehaving....

---

### Post by smurphy_it on 2008-01-18
Some new package or update could of broken your wifi setup, and it might have to be done again.  Are you using a native wifi driver, a restricted or a ndiswrapper setup for your wifi ?  What kind of chipset is it ?  Broadcom, atheros, dell, etc ?

If it's ndiswrapper, you could try removing the ndiswrapper and re-installing it.
Same goes for the restricted drivers.

native is probably a different ball of wax.

---

### Post by tennvolsmb on 2008-01-18
well i have a broadcom but I did try to disable my WEP and it still wouldn't work. I am using other computers on my home network through wi-fi. It's only my laptop running ubuntu that refuses to connect.

---

### Post by tennvolsmb on 2008-01-18
bump

---

