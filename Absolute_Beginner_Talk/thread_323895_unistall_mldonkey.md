---
title: "unistall mldonkey"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by bengar on 2006-12-22
Hello
Every time that I install a program the following message appears (attachament). I erased it with sudo apt-get remove mldonkey thats was done without problems, but the  message continue well I reinstall it and this is what appear  E: mldonkey-server: subprocess post-installation script returned error exit status 1, I unistall it from Synaptic package and this appear E: mldonkey-server: subprocess pre-installation script returned error exit status 1. Well a little of knowledge is better that nothing.

---

### Post by raul_ on 2006-12-22
It's still running in the background and probably still in the startup services. kill it and remove it from the startup services (maybe with boot manager under System->Preferences), log out, log in, and then try removing it again

---

### Post by bengar on 2006-12-22
Thanks Raul I will try it and report it later.

---

### Post by Rippey on 2006-12-22
this worked for me.
[https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42847](https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42847)

---

### Post by bengar on 2006-12-23
> **Rippey said:**
> this worked for me.
[https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42847](https://launchpad.net/distros/ubuntu/+source/mldonkey/+bug/42847)


Thanks rippey, I follow the instruction but a message pop up said. **Could not save the file /var/lib/dpkg/info/mldonkey-server.prerm. You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.**

---

### Post by Rippey on 2006-12-23
did you try editing the file as root?

---

